
```java 

package in.rkvsraman.archopsdemo;

import java.util.*;
import software.amazon.awscdk.core.*;
import software.amazon.awscdk.services.apigateway.*;
import software.amazon.awscdk.services.autoscaling.*;
import software.amazon.awscdk.services.ec2.*;
import software.amazon.awscdk.services.elasticloadbalancingv2.*;
import software.amazon.awscdk.services.rds.*;
import software.amazon.awsconstructs.services.cloudfrontapigateway.*;

public class ArchOpsDemo {
	public static software.amazon.awscdk.core.App app1;
	public static software.amazon.awscdk.core.Environment mainStackEnv;
	public static software.amazon.awscdk.core.Stack mainStack;
	public static software.amazon.awscdk.services.ec2.Vpc default_vpc;
	public static software.amazon.awscdk.services.ec2.Subnet subnetUS1A;
	public static software.amazon.awscdk.services.autoscaling.AutoScalingGroup autoScalingGroup16;
	public static software.amazon.awscdk.services.ec2.Subnet subnetUS1B;
	public static software.amazon.awscdk.services.apigateway.RestApi sampleRestAPI;
	public static software.amazon.awscdk.services.elasticloadbalancingv2.ApplicationLoadBalancer applicationLoadBalancer11;
	public static software.amazon.awsconstructs.services.cloudfrontapigateway.CloudFrontToApiGateway cloudfront_api_gateway;
	public static software.amazon.awscdk.services.apigateway.Method genericMethod;
	public static software.amazon.awscdk.services.rds.DatabaseInstance rdsBackend;

	public static void main(String args[]) {
		app1 = software.amazon.awscdk.core.App.Builder.create().autoSynth(true).runtimeInfo(true).stackTraces(true)
				.treeMetadata(true).build();

		mainStackEnv = (new software.amazon.awscdk.core.Environment.Builder()).region("us-east-1").build();

		mainStack = software.amazon.awscdk.core.Stack.Builder.create(app1, "MAINSTACK").env(mainStackEnv)
				.stackName("mainStack").terminationProtection(true).build();

		default_vpc = software.amazon.awscdk.services.ec2.Vpc.Builder.create(mainStack, "DEFAULT_VPC")
				.cidr("10.0. 0.0/16").enableDnsHostnames(true).enableDnsSupport(true).maxAzs(2).natGateways(1)
				.vpnGateway(true).build();

		subnetUS1A = software.amazon.awscdk.services.ec2.Subnet.Builder.create(mainStack, "SUBNETUS1A")
				.availabilityZone("us-east-1a").cidrBlock("10.0. 0.0/16").vpcId(default_vpc.getVpcId())
				.mapPublicIpOnLaunch(true).build();

		autoScalingGroup16 = software.amazon.awscdk.services.autoscaling.AutoScalingGroup.Builder
				.create(mainStack, "AUTOSCALINGGROUP16").allowAllOutbound(true).maxCapacity(2)
				.replacingUpdateMinSuccessfulInstancesPercent(20).resourceSignalCount(4)
				.instanceType(InstanceType.of(InstanceClass.BURSTABLE2, InstanceSize.MEDIUM))
				.machineImage(new AmazonLinuxImage()).vpc(default_vpc).build();

		subnetUS1B = software.amazon.awscdk.services.ec2.Subnet.Builder.create(mainStack, "SUBNETUS1B")
				.availabilityZone("us-east-1b").cidrBlock("10.0. 0.0/16").vpcId(default_vpc.getVpcId()).build();

		sampleRestAPI = software.amazon.awscdk.services.apigateway.RestApi.Builder.create(mainStack, "RESTAPI")
				.restApiName("sampleAPI").build();

		applicationLoadBalancer11 = software.amazon.awscdk.services.elasticloadbalancingv2.ApplicationLoadBalancer.Builder
				.create(mainStack, "APPLICATIONLOADBALANCER11").vpc(default_vpc).deletionProtection(true)
				.internetFacing(true).http2Enabled(true).build();

		cloudfront_api_gateway = software.amazon.awsconstructs.services.cloudfrontapigateway.CloudFrontToApiGateway.Builder
				.create(mainStack, "CLOUDFRONT_API_GATEWAY").existingApiGatewayObj(sampleRestAPI).build();

		genericMethod = software.amazon.awscdk.services.apigateway.Method.Builder.create(mainStack, "GENERICMETHOD")
				.httpMethod("ANY").resource(sampleRestAPI.getRoot()).build();

		rdsBackend = software.amazon.awscdk.services.rds.DatabaseInstance.Builder.create(mainStack, "RDSBACKEND")
				.vpc(default_vpc).deleteAutomatedBackups(true).deletionProtection(true).iops(1200).multiAz(true)
				.port(3306).engine(DatabaseInstanceEngine.MYSQL).databaseName("mysqlMainDB").masterUsername("root")
				.build();

		ArchOpsDemoHelper.setup();
		app1.synth();
	}
}
```
