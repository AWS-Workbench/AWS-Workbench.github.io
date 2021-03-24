
```json
{
  "Resources": {
    "DEFAULTVPCCF30E75C": {
      "Type": "AWS::EC2::VPC",
      "Properties": {
        "CidrBlock": "10.0. 0.0/16",
        "EnableDnsHostnames": true,
        "EnableDnsSupport": true,
        "InstanceTenancy": "default",
        "Tags": [
          {
            "Key": "Name",
            "Value": "MAINSTACK/DEFAULT_VPC"
          }
        ]
      },
      "Metadata": {
        "aws:cdk:path": "MAINSTACK/DEFAULT_VPC/Resource"
      }
    },
    "DEFAULTVPCPublicSubnet1Subnet3FA22A5D": {
      "Type": "AWS::EC2::Subnet",
      "Properties": {
        "CidrBlock": "10.0.0.0/18",
        "VpcId": {
          "Ref": "DEFAULTVPCCF30E75C"
        },
        "AvailabilityZone": {
          "Fn::Select": [
            0,
            {
              "Fn::GetAZs": ""
            }
          ]
        },
        "MapPublicIpOnLaunch": true,
        "Tags": [
          {
            "Key": "aws-cdk:subnet-name",
            "Value": "Public"
          },
          {
            "Key": "aws-cdk:subnet-type",
            "Value": "Public"
          },
          {
            "Key": "Name",
            "Value": "MAINSTACK/DEFAULT_VPC/PublicSubnet1"
          }
        ]
      },
      "Metadata": {
        "aws:cdk:path": "MAINSTACK/DEFAULT_VPC/PublicSubnet1/Subnet"
      }
    },
    "DEFAULTVPCPublicSubnet1RouteTable9B0F2D0E": {
      "Type": "AWS::EC2::RouteTable",
      "Properties": {
        "VpcId": {
          "Ref": "DEFAULTVPCCF30E75C"
        },
        "Tags": [
          {
            "Key": "Name",
            "Value": "MAINSTACK/DEFAULT_VPC/PublicSubnet1"
          }
        ]
      },
      "Metadata": {
        "aws:cdk:path": "MAINSTACK/DEFAULT_VPC/PublicSubnet1/RouteTable"
      }
    },
    "DEFAULTVPCPublicSubnet1RouteTableAssociationD2BB5E75": {
      "Type": "AWS::EC2::SubnetRouteTableAssociation",
      "Properties": {
        "RouteTableId": {
          "Ref": "DEFAULTVPCPublicSubnet1RouteTable9B0F2D0E"
        },
        "SubnetId": {
          "Ref": "DEFAULTVPCPublicSubnet1Subnet3FA22A5D"
        }
      },
      "Metadata": {
        "aws:cdk:path": "MAINSTACK/DEFAULT_VPC/PublicSubnet1/RouteTableAssociation"
      }
    },
    "DEFAULTVPCPublicSubnet1DefaultRouteC3757082": {
      "Type": "AWS::EC2::Route",
      "Properties": {
        "RouteTableId": {
          "Ref": "DEFAULTVPCPublicSubnet1RouteTable9B0F2D0E"
        },
        "DestinationCidrBlock": "0.0.0.0/0",
        "GatewayId": {
          "Ref": "DEFAULTVPCIGW12EF59E6"
        }
      },
      "DependsOn": [
        "DEFAULTVPCVPCGWBED7D3F5"
      ],
      "Metadata": {
        "aws:cdk:path": "MAINSTACK/DEFAULT_VPC/PublicSubnet1/DefaultRoute"
      }
    },
    "DEFAULTVPCPublicSubnet1EIP02A863CC": {
      "Type": "AWS::EC2::EIP",
      "Properties": {
        "Domain": "vpc",
        "Tags": [
          {
            "Key": "Name",
            "Value": "MAINSTACK/DEFAULT_VPC/PublicSubnet1"
          }
        ]
      },
      "Metadata": {
        "aws:cdk:path": "MAINSTACK/DEFAULT_VPC/PublicSubnet1/EIP"
      }
    },
    "DEFAULTVPCPublicSubnet1NATGateway36EF4C2F": {
      "Type": "AWS::EC2::NatGateway",
      "Properties": {
        "AllocationId": {
          "Fn::GetAtt": [
            "DEFAULTVPCPublicSubnet1EIP02A863CC",
            "AllocationId"
          ]
        },
        "SubnetId": {
          "Ref": "DEFAULTVPCPublicSubnet1Subnet3FA22A5D"
        },
        "Tags": [
          {
            "Key": "Name",
            "Value": "MAINSTACK/DEFAULT_VPC/PublicSubnet1"
          }
        ]
      },
      "Metadata": {
        "aws:cdk:path": "MAINSTACK/DEFAULT_VPC/PublicSubnet1/NATGateway"
      }
    },
    "DEFAULTVPCPublicSubnet2Subnet2F02D8F0": {
      "Type": "AWS::EC2::Subnet",
      "Properties": {
        "CidrBlock": "10.0.64.0/18",
        "VpcId": {
          "Ref": "DEFAULTVPCCF30E75C"
        },
        "AvailabilityZone": {
          "Fn::Select": [
            1,
            {
              "Fn::GetAZs": ""
            }
          ]
        },
        "MapPublicIpOnLaunch": true,
        "Tags": [
          {
            "Key": "aws-cdk:subnet-name",
            "Value": "Public"
          },
          {
            "Key": "aws-cdk:subnet-type",
            "Value": "Public"
          },
          {
            "Key": "Name",
            "Value": "MAINSTACK/DEFAULT_VPC/PublicSubnet2"
          }
        ]
      },
      "Metadata": {
        "aws:cdk:path": "MAINSTACK/DEFAULT_VPC/PublicSubnet2/Subnet"
      }
    },
    "DEFAULTVPCPublicSubnet2RouteTable5D3E76A8": {
      "Type": "AWS::EC2::RouteTable",
      "Properties": {
        "VpcId": {
          "Ref": "DEFAULTVPCCF30E75C"
        },
        "Tags": [
          {
            "Key": "Name",
            "Value": "MAINSTACK/DEFAULT_VPC/PublicSubnet2"
          }
        ]
      },
      "Metadata": {
        "aws:cdk:path": "MAINSTACK/DEFAULT_VPC/PublicSubnet2/RouteTable"
      }
    },
    "DEFAULTVPCPublicSubnet2RouteTableAssociationA7130E67": {
      "Type": "AWS::EC2::SubnetRouteTableAssociation",
      "Properties": {
        "RouteTableId": {
          "Ref": "DEFAULTVPCPublicSubnet2RouteTable5D3E76A8"
        },
        "SubnetId": {
          "Ref": "DEFAULTVPCPublicSubnet2Subnet2F02D8F0"
        }
      },
      "Metadata": {
        "aws:cdk:path": "MAINSTACK/DEFAULT_VPC/PublicSubnet2/RouteTableAssociation"
      }
    },
    "DEFAULTVPCPublicSubnet2DefaultRouteF032EC70": {
      "Type": "AWS::EC2::Route",
      "Properties": {
        "RouteTableId": {
          "Ref": "DEFAULTVPCPublicSubnet2RouteTable5D3E76A8"
        },
        "DestinationCidrBlock": "0.0.0.0/0",
        "GatewayId": {
          "Ref": "DEFAULTVPCIGW12EF59E6"
        }
      },
      "DependsOn": [
        "DEFAULTVPCVPCGWBED7D3F5"
      ],
      "Metadata": {
        "aws:cdk:path": "MAINSTACK/DEFAULT_VPC/PublicSubnet2/DefaultRoute"
      }
    },
    "DEFAULTVPCPrivateSubnet1SubnetF3907A35": {
      "Type": "AWS::EC2::Subnet",
      "Properties": {
        "CidrBlock": "10.0.128.0/18",
        "VpcId": {
          "Ref": "DEFAULTVPCCF30E75C"
        },
        "AvailabilityZone": {
          "Fn::Select": [
            0,
            {
              "Fn::GetAZs": ""
            }
          ]
        },
        "MapPublicIpOnLaunch": false,
        "Tags": [
          {
            "Key": "aws-cdk:subnet-name",
            "Value": "Private"
          },
          {
            "Key": "aws-cdk:subnet-type",
            "Value": "Private"
          },
          {
            "Key": "Name",
            "Value": "MAINSTACK/DEFAULT_VPC/PrivateSubnet1"
          }
        ]
      },
      "Metadata": {
        "aws:cdk:path": "MAINSTACK/DEFAULT_VPC/PrivateSubnet1/Subnet"
      }
    },
    "DEFAULTVPCPrivateSubnet1RouteTable90478756": {
      "Type": "AWS::EC2::RouteTable",
      "Properties": {
        "VpcId": {
          "Ref": "DEFAULTVPCCF30E75C"
        },
        "Tags": [
          {
            "Key": "Name",
            "Value": "MAINSTACK/DEFAULT_VPC/PrivateSubnet1"
          }
        ]
      },
      "Metadata": {
        "aws:cdk:path": "MAINSTACK/DEFAULT_VPC/PrivateSubnet1/RouteTable"
      }
    },
    "DEFAULTVPCPrivateSubnet1RouteTableAssociationD37C5FCD": {
      "Type": "AWS::EC2::SubnetRouteTableAssociation",
      "Properties": {
        "RouteTableId": {
          "Ref": "DEFAULTVPCPrivateSubnet1RouteTable90478756"
        },
        "SubnetId": {
          "Ref": "DEFAULTVPCPrivateSubnet1SubnetF3907A35"
        }
      },
      "Metadata": {
        "aws:cdk:path": "MAINSTACK/DEFAULT_VPC/PrivateSubnet1/RouteTableAssociation"
      }
    },
    "DEFAULTVPCPrivateSubnet1DefaultRouteA40C15A5": {
      "Type": "AWS::EC2::Route",
      "Properties": {
        "RouteTableId": {
          "Ref": "DEFAULTVPCPrivateSubnet1RouteTable90478756"
        },
        "DestinationCidrBlock": "0.0.0.0/0",
        "NatGatewayId": {
          "Ref": "DEFAULTVPCPublicSubnet1NATGateway36EF4C2F"
        }
      },
      "Metadata": {
        "aws:cdk:path": "MAINSTACK/DEFAULT_VPC/PrivateSubnet1/DefaultRoute"
      }
    },
    "DEFAULTVPCPrivateSubnet2Subnet1F8B1A7D": {
      "Type": "AWS::EC2::Subnet",
      "Properties": {
        "CidrBlock": "10.0.192.0/18",
        "VpcId": {
          "Ref": "DEFAULTVPCCF30E75C"
        },
        "AvailabilityZone": {
          "Fn::Select": [
            1,
            {
              "Fn::GetAZs": ""
            }
          ]
        },
        "MapPublicIpOnLaunch": false,
        "Tags": [
          {
            "Key": "aws-cdk:subnet-name",
            "Value": "Private"
          },
          {
            "Key": "aws-cdk:subnet-type",
            "Value": "Private"
          },
          {
            "Key": "Name",
            "Value": "MAINSTACK/DEFAULT_VPC/PrivateSubnet2"
          }
        ]
      },
      "Metadata": {
        "aws:cdk:path": "MAINSTACK/DEFAULT_VPC/PrivateSubnet2/Subnet"
      }
    },
    "DEFAULTVPCPrivateSubnet2RouteTableB00D4115": {
      "Type": "AWS::EC2::RouteTable",
      "Properties": {
        "VpcId": {
          "Ref": "DEFAULTVPCCF30E75C"
        },
        "Tags": [
          {
            "Key": "Name",
            "Value": "MAINSTACK/DEFAULT_VPC/PrivateSubnet2"
          }
        ]
      },
      "Metadata": {
        "aws:cdk:path": "MAINSTACK/DEFAULT_VPC/PrivateSubnet2/RouteTable"
      }
    },
    "DEFAULTVPCPrivateSubnet2RouteTableAssociation4A516F35": {
      "Type": "AWS::EC2::SubnetRouteTableAssociation",
      "Properties": {
        "RouteTableId": {
          "Ref": "DEFAULTVPCPrivateSubnet2RouteTableB00D4115"
        },
        "SubnetId": {
          "Ref": "DEFAULTVPCPrivateSubnet2Subnet1F8B1A7D"
        }
      },
      "Metadata": {
        "aws:cdk:path": "MAINSTACK/DEFAULT_VPC/PrivateSubnet2/RouteTableAssociation"
      }
    },
    "DEFAULTVPCPrivateSubnet2DefaultRoute7F339CAE": {
      "Type": "AWS::EC2::Route",
      "Properties": {
        "RouteTableId": {
          "Ref": "DEFAULTVPCPrivateSubnet2RouteTableB00D4115"
        },
        "DestinationCidrBlock": "0.0.0.0/0",
        "NatGatewayId": {
          "Ref": "DEFAULTVPCPublicSubnet1NATGateway36EF4C2F"
        }
      },
      "Metadata": {
        "aws:cdk:path": "MAINSTACK/DEFAULT_VPC/PrivateSubnet2/DefaultRoute"
      }
    },
    "DEFAULTVPCIGW12EF59E6": {
      "Type": "AWS::EC2::InternetGateway",
      "Properties": {
        "Tags": [
          {
            "Key": "Name",
            "Value": "MAINSTACK/DEFAULT_VPC"
          }
        ]
      },
      "Metadata": {
        "aws:cdk:path": "MAINSTACK/DEFAULT_VPC/IGW"
      }
    },
    "DEFAULTVPCVPCGWBED7D3F5": {
      "Type": "AWS::EC2::VPCGatewayAttachment",
      "Properties": {
        "VpcId": {
          "Ref": "DEFAULTVPCCF30E75C"
        },
        "InternetGatewayId": {
          "Ref": "DEFAULTVPCIGW12EF59E6"
        }
      },
      "Metadata": {
        "aws:cdk:path": "MAINSTACK/DEFAULT_VPC/VPCGW"
      }
    },
    "DEFAULTVPCVpnGatewayBB0F6302": {
      "Type": "AWS::EC2::VPNGateway",
      "Properties": {
        "Type": "ipsec.1",
        "Tags": [
          {
            "Key": "Name",
            "Value": "MAINSTACK/DEFAULT_VPC"
          }
        ]
      },
      "Metadata": {
        "aws:cdk:path": "MAINSTACK/DEFAULT_VPC/VpnGateway/Default"
      }
    },
    "DEFAULTVPCVPCVPNGW344C3A03": {
      "Type": "AWS::EC2::VPCGatewayAttachment",
      "Properties": {
        "VpcId": {
          "Ref": "DEFAULTVPCCF30E75C"
        },
        "VpnGatewayId": {
          "Ref": "DEFAULTVPCVpnGatewayBB0F6302"
        }
      },
      "Metadata": {
        "aws:cdk:path": "MAINSTACK/DEFAULT_VPC/VPCVPNGW"
      }
    },
    "DEFAULTVPCRoutePropagationF5A157DE": {
      "Type": "AWS::EC2::VPNGatewayRoutePropagation",
      "Properties": {
        "RouteTableIds": [
          {
            "Ref": "DEFAULTVPCPrivateSubnet1RouteTable90478756"
          },
          {
            "Ref": "DEFAULTVPCPrivateSubnet2RouteTableB00D4115"
          }
        ],
        "VpnGatewayId": {
          "Ref": "DEFAULTVPCVpnGatewayBB0F6302"
        }
      },
      "DependsOn": [
        "DEFAULTVPCVPCVPNGW344C3A03"
      ],
      "Metadata": {
        "aws:cdk:path": "MAINSTACK/DEFAULT_VPC/RoutePropagation"
      }
    },
    "SUBNETUS1ASubnetC3C76920": {
      "Type": "AWS::EC2::Subnet",
      "Properties": {
        "CidrBlock": "10.0. 0.0/16",
        "VpcId": {
          "Ref": "DEFAULTVPCCF30E75C"
        },
        "AvailabilityZone": "us-east-1a",
        "MapPublicIpOnLaunch": true,
        "Tags": [
          {
            "Key": "Name",
            "Value": "MAINSTACK/SUBNETUS1A"
          }
        ]
      },
      "Metadata": {
        "aws:cdk:path": "MAINSTACK/SUBNETUS1A/Subnet"
      }
    },
    "SUBNETUS1ARouteTable6F636FAC": {
      "Type": "AWS::EC2::RouteTable",
      "Properties": {
        "VpcId": {
          "Ref": "DEFAULTVPCCF30E75C"
        },
        "Tags": [
          {
            "Key": "Name",
            "Value": "MAINSTACK/SUBNETUS1A"
          }
        ]
      },
      "Metadata": {
        "aws:cdk:path": "MAINSTACK/SUBNETUS1A/RouteTable"
      }
    },
    "SUBNETUS1ARouteTableAssociation7CD51AC9": {
      "Type": "AWS::EC2::SubnetRouteTableAssociation",
      "Properties": {
        "RouteTableId": {
          "Ref": "SUBNETUS1ARouteTable6F636FAC"
        },
        "SubnetId": {
          "Ref": "SUBNETUS1ASubnetC3C76920"
        }
      },
      "Metadata": {
        "aws:cdk:path": "MAINSTACK/SUBNETUS1A/RouteTableAssociation"
      }
    },
    "AUTOSCALINGGROUP16InstanceSecurityGroup5AECE231": {
      "Type": "AWS::EC2::SecurityGroup",
      "Properties": {
        "GroupDescription": "MAINSTACK/AUTOSCALINGGROUP16/InstanceSecurityGroup",
        "SecurityGroupEgress": [
          {
            "CidrIp": "0.0.0.0/0",
            "Description": "Allow all outbound traffic by default",
            "IpProtocol": "-1"
          }
        ],
        "Tags": [
          {
            "Key": "Name",
            "Value": "MAINSTACK/AUTOSCALINGGROUP16"
          }
        ],
        "VpcId": {
          "Ref": "DEFAULTVPCCF30E75C"
        }
      },
      "Metadata": {
        "aws:cdk:path": "MAINSTACK/AUTOSCALINGGROUP16/InstanceSecurityGroup/Resource"
      }
    },
    "AUTOSCALINGGROUP16InstanceRoleDB596AA6": {
      "Type": "AWS::IAM::Role",
      "Properties": {
        "AssumeRolePolicyDocument": {
          "Statement": [
            {
              "Action": "sts:AssumeRole",
              "Effect": "Allow",
              "Principal": {
                "Service": "ec2.amazonaws.com"
              }
            }
          ],
          "Version": "2012-10-17"
        },
        "Tags": [
          {
            "Key": "Name",
            "Value": "MAINSTACK/AUTOSCALINGGROUP16"
          }
        ]
      },
      "Metadata": {
        "aws:cdk:path": "MAINSTACK/AUTOSCALINGGROUP16/InstanceRole/Resource"
      }
    },
    "AUTOSCALINGGROUP16InstanceProfileACEF21A7": {
      "Type": "AWS::IAM::InstanceProfile",
      "Properties": {
        "Roles": [
          {
            "Ref": "AUTOSCALINGGROUP16InstanceRoleDB596AA6"
          }
        ]
      },
      "Metadata": {
        "aws:cdk:path": "MAINSTACK/AUTOSCALINGGROUP16/InstanceProfile"
      }
    },
    "AUTOSCALINGGROUP16LaunchConfigA22B8EEE": {
      "Type": "AWS::AutoScaling::LaunchConfiguration",
      "Properties": {
        "ImageId": {
          "Ref": "SsmParameterValueawsserviceamiamazonlinuxlatestamznamihvmx8664gp2C96584B6F00A464EAD1953AFF4B05118Parameter"
        },
        "InstanceType": "t2.medium",
        "IamInstanceProfile": {
          "Ref": "AUTOSCALINGGROUP16InstanceProfileACEF21A7"
        },
        "SecurityGroups": [
          {
            "Fn::GetAtt": [
              "AUTOSCALINGGROUP16InstanceSecurityGroup5AECE231",
              "GroupId"
            ]
          }
        ],
        "UserData": {
          "Fn::Base64": "#!/bin/bash"
        }
      },
      "DependsOn": [
        "AUTOSCALINGGROUP16InstanceRoleDB596AA6"
      ],
      "Metadata": {
        "aws:cdk:path": "MAINSTACK/AUTOSCALINGGROUP16/LaunchConfig"
      }
    },
    "AUTOSCALINGGROUP16ASG1FE8AC2E": {
      "Type": "AWS::AutoScaling::AutoScalingGroup",
      "Properties": {
        "MaxSize": "2",
        "MinSize": "1",
        "LaunchConfigurationName": {
          "Ref": "AUTOSCALINGGROUP16LaunchConfigA22B8EEE"
        },
        "Tags": [
          {
            "Key": "Name",
            "PropagateAtLaunch": true,
            "Value": "MAINSTACK/AUTOSCALINGGROUP16"
          }
        ],
        "VPCZoneIdentifier": [
          {
            "Ref": "DEFAULTVPCPrivateSubnet1SubnetF3907A35"
          },
          {
            "Ref": "DEFAULTVPCPrivateSubnet2Subnet1F8B1A7D"
          }
        ]
      },
      "CreationPolicy": {
        "ResourceSignal": {
          "Count": 4
        }
      },
      "UpdatePolicy": {
        "AutoScalingScheduledAction": {
          "IgnoreUnmodifiedGroupSizeProperties": true
        }
      },
      "Metadata": {
        "aws:cdk:path": "MAINSTACK/AUTOSCALINGGROUP16/ASG"
      }
    },
    "SUBNETUS1BSubnetE0B645F1": {
      "Type": "AWS::EC2::Subnet",
      "Properties": {
        "CidrBlock": "10.0. 0.0/16",
        "VpcId": {
          "Ref": "DEFAULTVPCCF30E75C"
        },
        "AvailabilityZone": "us-east-1b",
        "Tags": [
          {
            "Key": "Name",
            "Value": "MAINSTACK/SUBNETUS1B"
          }
        ]
      },
      "Metadata": {
        "aws:cdk:path": "MAINSTACK/SUBNETUS1B/Subnet"
      }
    },
    "SUBNETUS1BRouteTable7ADAD7C6": {
      "Type": "AWS::EC2::RouteTable",
      "Properties": {
        "VpcId": {
          "Ref": "DEFAULTVPCCF30E75C"
        },
        "Tags": [
          {
            "Key": "Name",
            "Value": "MAINSTACK/SUBNETUS1B"
          }
        ]
      },
      "Metadata": {
        "aws:cdk:path": "MAINSTACK/SUBNETUS1B/RouteTable"
      }
    },
    "SUBNETUS1BRouteTableAssociationACD7F587": {
      "Type": "AWS::EC2::SubnetRouteTableAssociation",
      "Properties": {
        "RouteTableId": {
          "Ref": "SUBNETUS1BRouteTable7ADAD7C6"
        },
        "SubnetId": {
          "Ref": "SUBNETUS1BSubnetE0B645F1"
        }
      },
      "Metadata": {
        "aws:cdk:path": "MAINSTACK/SUBNETUS1B/RouteTableAssociation"
      }
    },
    "RESTAPIF36BC7AE": {
      "Type": "AWS::ApiGateway::RestApi",
      "Properties": {
        "Name": "sampleAPI"
      },
      "Metadata": {
        "aws:cdk:path": "MAINSTACK/RESTAPI/Resource"
      }
    },
    "RESTAPICloudWatchRoleC1DA9DD1": {
      "Type": "AWS::IAM::Role",
      "Properties": {
        "AssumeRolePolicyDocument": {
          "Statement": [
            {
              "Action": "sts:AssumeRole",
              "Effect": "Allow",
              "Principal": {
                "Service": "apigateway.amazonaws.com"
              }
            }
          ],
          "Version": "2012-10-17"
        },
        "ManagedPolicyArns": [
          {
            "Fn::Join": [
              "",
              [
                "arn:",
                {
                  "Ref": "AWS::Partition"
                },
                ":iam::aws:policy/service-role/AmazonAPIGatewayPushToCloudWatchLogs"
              ]
            ]
          }
        ]
      },
      "Metadata": {
        "aws:cdk:path": "MAINSTACK/RESTAPI/CloudWatchRole/Resource"
      }
    },
    "RESTAPIAccount39826DFC": {
      "Type": "AWS::ApiGateway::Account",
      "Properties": {
        "CloudWatchRoleArn": {
          "Fn::GetAtt": [
            "RESTAPICloudWatchRoleC1DA9DD1",
            "Arn"
          ]
        }
      },
      "DependsOn": [
        "RESTAPIF36BC7AE"
      ],
      "Metadata": {
        "aws:cdk:path": "MAINSTACK/RESTAPI/Account"
      }
    },
    "RESTAPIDeploymentC43CA37A13268fde8e6d7851f9b5c71948144ac1": {
      "Type": "AWS::ApiGateway::Deployment",
      "Properties": {
        "RestApiId": {
          "Ref": "RESTAPIF36BC7AE"
        },
        "Description": "Automatically created by the RestApi construct"
      },
      "DependsOn": [
        "GENERICMETHOD7AEC1F4A"
      ],
      "Metadata": {
        "aws:cdk:path": "MAINSTACK/RESTAPI/Deployment/Resource"
      }
    },
    "RESTAPIDeploymentStageprod63DE3AD3": {
      "Type": "AWS::ApiGateway::Stage",
      "Properties": {
        "RestApiId": {
          "Ref": "RESTAPIF36BC7AE"
        },
        "DeploymentId": {
          "Ref": "RESTAPIDeploymentC43CA37A13268fde8e6d7851f9b5c71948144ac1"
        },
        "StageName": "prod"
      },
      "Metadata": {
        "aws:cdk:path": "MAINSTACK/RESTAPI/DeploymentStage.prod/Resource"
      }
    },
    "APPLICATIONLOADBALANCER11184218D8": {
      "Type": "AWS::ElasticLoadBalancingV2::LoadBalancer",
      "Properties": {
        "LoadBalancerAttributes": [
          {
            "Key": "deletion_protection.enabled",
            "Value": "true"
          }
        ],
        "Scheme": "internet-facing",
        "SecurityGroups": [
          {
            "Fn::GetAtt": [
              "APPLICATIONLOADBALANCER11SecurityGroup6AB704A9",
              "GroupId"
            ]
          }
        ],
        "Subnets": [
          {
            "Ref": "DEFAULTVPCPublicSubnet1Subnet3FA22A5D"
          },
          {
            "Ref": "DEFAULTVPCPublicSubnet2Subnet2F02D8F0"
          }
        ],
        "Type": "application"
      },
      "DependsOn": [
        "DEFAULTVPCPublicSubnet1DefaultRouteC3757082",
        "DEFAULTVPCPublicSubnet2DefaultRouteF032EC70"
      ],
      "Metadata": {
        "aws:cdk:path": "MAINSTACK/APPLICATIONLOADBALANCER11/Resource"
      }
    },
    "APPLICATIONLOADBALANCER11SecurityGroup6AB704A9": {
      "Type": "AWS::EC2::SecurityGroup",
      "Properties": {
        "GroupDescription": "Automatically created Security Group for ELB MAINSTACKAPPLICATIONLOADBALANCER1156882521",
        "SecurityGroupEgress": [
          {
            "CidrIp": "255.255.255.255/32",
            "Description": "Disallow all traffic",
            "FromPort": 252,
            "IpProtocol": "icmp",
            "ToPort": 86
          }
        ],
        "VpcId": {
          "Ref": "DEFAULTVPCCF30E75C"
        }
      },
      "Metadata": {
        "aws:cdk:path": "MAINSTACK/APPLICATIONLOADBALANCER11/SecurityGroup/Resource"
      }
    },
    "CLOUDFRONTAPIGATEWAYSetHttpSecurityHeadersServiceRoleA3062476": {
      "Type": "AWS::IAM::Role",
      "Properties": {
        "AssumeRolePolicyDocument": {
          "Statement": [
            {
              "Action": "sts:AssumeRole",
              "Effect": "Allow",
              "Principal": {
                "Service": "lambda.amazonaws.com"
              }
            },
            {
              "Action": "sts:AssumeRole",
              "Effect": "Allow",
              "Principal": {
                "Service": "edgelambda.amazonaws.com"
              }
            }
          ],
          "Version": "2012-10-17"
        },
        "Policies": [
          {
            "PolicyDocument": {
              "Statement": [
                {
                  "Action": [
                    "logs:CreateLogGroup",
                    "logs:CreateLogStream",
                    "logs:PutLogEvents"
                  ],
                  "Effect": "Allow",
                  "Resource": {
                    "Fn::Join": [
                      "",
                      [
                        "arn:aws:logs:",
                        {
                          "Ref": "AWS::Region"
                        },
                        ":",
                        {
                          "Ref": "AWS::AccountId"
                        },
                        ":log-group:/aws/lambda/*"
                      ]
                    ]
                  }
                }
              ],
              "Version": "2012-10-17"
            },
            "PolicyName": "LambdaFunctionServiceRolePolicy"
          }
        ]
      },
      "Metadata": {
        "aws:cdk:path": "MAINSTACK/CLOUDFRONT_API_GATEWAY/SetHttpSecurityHeadersServiceRole/Resource"
      }
    },
    "CLOUDFRONTAPIGATEWAYSetHttpSecurityHeaders27D16B5F": {
      "Type": "AWS::Lambda::Function",
      "Properties": {
        "Code": {
          "ZipFile": "exports.handler = (event, context, callback) => {           const response = event.Records[0].cf.response;           const headers = response.headers;           headers['x-xss-protection'] = [             {               key: 'X-XSS-Protection',               value: '1; mode=block'             }           ];           headers['x-frame-options'] = [             {               key: 'X-Frame-Options',               value: 'DENY'             }           ];           headers['x-content-type-options'] = [             {               key: 'X-Content-Type-Options',               value: 'nosniff'             }           ];           headers['strict-transport-security'] = [             {               key: 'Strict-Transport-Security',               value: 'max-age=63072000; includeSubdomains; preload'             }           ];           headers['referrer-policy'] = [             {               key: 'Referrer-Policy',               value: 'same-origin'             }           ];           headers['content-security-policy'] = [             {               key: 'Content-Security-Policy',               value: \"default-src 'none'; base-uri 'self'; img-src 'self'; script-src 'self'; style-src 'self' https:; object-src 'none'; frame-ancestors 'none'; font-src 'self' https:; form-action 'self'; manifest-src 'self'; connect-src 'self'\"              }           ];           callback(null, response);         };"
        },
        "Handler": "index.handler",
        "Role": {
          "Fn::GetAtt": [
            "CLOUDFRONTAPIGATEWAYSetHttpSecurityHeadersServiceRoleA3062476",
            "Arn"
          ]
        },
        "Runtime": "nodejs12.x"
      },
      "DependsOn": [
        "CLOUDFRONTAPIGATEWAYSetHttpSecurityHeadersServiceRoleA3062476"
      ],
      "Metadata": {
        "cfn_nag": {
          "rules_to_suppress": [
            {
              "id": "W58",
              "reason": "Lambda functions has the required permission to write CloudWatch Logs. It uses custom policy instead of arn:aws:iam::aws:policy/service-role/AWSLambdaBasicExecutionRole with more tighter permissions."
            }
          ]
        }
      }
    },
    "CLOUDFRONTAPIGATEWAYSetHttpSecurityHeadersVersion0EA4F824": {
      "Type": "AWS::Lambda::Version",
      "Properties": {
        "FunctionName": {
          "Ref": "CLOUDFRONTAPIGATEWAYSetHttpSecurityHeaders27D16B5F"
        }
      },
      "Metadata": {
        "aws:cdk:path": "MAINSTACK/CLOUDFRONT_API_GATEWAY/SetHttpSecurityHeadersVersion/Resource"
      }
    },
    "CLOUDFRONTAPIGATEWAYCloudfrontLoggingBucket4711BF7F": {
      "Type": "AWS::S3::Bucket",
      "Properties": {
        "AccessControl": "LogDeliveryWrite",
        "BucketEncryption": {
          "ServerSideEncryptionConfiguration": [
            {
              "ServerSideEncryptionByDefault": {
                "SSEAlgorithm": "AES256"
              }
            }
          ]
        },
        "PublicAccessBlockConfiguration": {
          "BlockPublicAcls": true,
          "BlockPublicPolicy": true,
          "IgnorePublicAcls": true,
          "RestrictPublicBuckets": true
        },
        "VersioningConfiguration": {
          "Status": "Enabled"
        }
      },
      "UpdateReplacePolicy": "Retain",
      "DeletionPolicy": "Retain",
      "Metadata": {
        "cfn_nag": {
          "rules_to_suppress": [
            {
              "id": "W35",
              "reason": "This S3 bucket is used as the access logging bucket for CloudFront Distribution"
            }
          ]
        }
      }
    },
    "CLOUDFRONTAPIGATEWAYCloudfrontLoggingBucketPolicy31EB75DD": {
      "Type": "AWS::S3::BucketPolicy",
      "Properties": {
        "Bucket": {
          "Ref": "CLOUDFRONTAPIGATEWAYCloudfrontLoggingBucket4711BF7F"
        },
        "PolicyDocument": {
          "Statement": [
            {
              "Action": "*",
              "Condition": {
                "Bool": {
                  "aws:SecureTransport": "false"
                }
              },
              "Effect": "Deny",
              "Principal": "*",
              "Resource": {
                "Fn::Join": [
                  "",
                  [
                    {
                      "Fn::GetAtt": [
                        "CLOUDFRONTAPIGATEWAYCloudfrontLoggingBucket4711BF7F",
                        "Arn"
                      ]
                    },
                    "/*"
                  ]
                ]
              },
              "Sid": "HttpsOnly"
            }
          ],
          "Version": "2012-10-17"
        }
      },
      "Metadata": {
        "aws:cdk:path": "MAINSTACK/CLOUDFRONT_API_GATEWAY/CloudfrontLoggingBucket/Policy/Resource"
      }
    },
    "CLOUDFRONTAPIGATEWAYCloudFrontDistributionCFDistribution5D78AEAE": {
      "Type": "AWS::CloudFront::Distribution",
      "Properties": {
        "DistributionConfig": {
          "DefaultCacheBehavior": {
            "AllowedMethods": [
              "GET",
              "HEAD"
            ],
            "CachedMethods": [
              "GET",
              "HEAD"
            ],
            "Compress": true,
            "ForwardedValues": {
              "Cookies": {
                "Forward": "none"
              },
              "QueryString": false
            },
            "LambdaFunctionAssociations": [
              {
                "EventType": "origin-response",
                "LambdaFunctionARN": {
                  "Ref": "CLOUDFRONTAPIGATEWAYSetHttpSecurityHeadersVersion0EA4F824"
                }
              }
            ],
            "TargetOriginId": "origin1",
            "ViewerProtocolPolicy": "redirect-to-https"
          },
          "DefaultRootObject": "index.html",
          "Enabled": true,
          "HttpVersion": "http2",
          "IPV6Enabled": true,
          "Logging": {
            "Bucket": {
              "Fn::GetAtt": [
                "CLOUDFRONTAPIGATEWAYCloudfrontLoggingBucket4711BF7F",
                "RegionalDomainName"
              ]
            },
            "IncludeCookies": false
          },
          "Origins": [
            {
              "ConnectionAttempts": 3,
              "ConnectionTimeout": 10,
              "CustomOriginConfig": {
                "HTTPPort": 80,
                "HTTPSPort": 443,
                "OriginKeepaliveTimeout": 5,
                "OriginProtocolPolicy": "https-only",
                "OriginReadTimeout": 30,
                "OriginSSLProtocols": [
                  "TLSv1.2"
                ]
              },
              "DomainName": {
                "Fn::Select": [
                  0,
                  {
                    "Fn::Split": [
                      "/",
                      {
                        "Fn::Select": [
                          1,
                          {
                            "Fn::Split": [
                              "://",
                              {
                                "Fn::Join": [
                                  "",
                                  [
                                    "https://",
                                    {
                                      "Ref": "RESTAPIF36BC7AE"
                                    },
                                    ".execute-api.us-east-1.",
                                    {
                                      "Ref": "AWS::URLSuffix"
                                    },
                                    "/",
                                    {
                                      "Ref": "RESTAPIDeploymentStageprod63DE3AD3"
                                    },
                                    "/"
                                  ]
                                ]
                              }
                            ]
                          }
                        ]
                      }
                    ]
                  }
                ]
              },
              "Id": "origin1"
            }
          ],
          "PriceClass": "PriceClass_100",
          "ViewerCertificate": {
            "CloudFrontDefaultCertificate": true
          }
        }
      },
      "Metadata": {
        "cfn_nag": {
          "rules_to_suppress": [
            {
              "id": "W70",
              "reason": "Since the distribution uses the CloudFront domain name, CloudFront automatically sets the security policy to TLSv1 regardless of the value of MinimumProtocolVersion"
            }
          ]
        }
      }
    },
    "GENERICMETHOD7AEC1F4A": {
      "Type": "AWS::ApiGateway::Method",
      "Properties": {
        "HttpMethod": "ANY",
        "ResourceId": {
          "Fn::GetAtt": [
            "RESTAPIF36BC7AE",
            "RootResourceId"
          ]
        },
        "RestApiId": {
          "Ref": "RESTAPIF36BC7AE"
        },
        "AuthorizationType": "NONE",
        "Integration": {
          "Type": "MOCK"
        }
      },
      "Metadata": {
        "aws:cdk:path": "MAINSTACK/GENERICMETHOD/Resource"
      }
    },
    "RDSBACKENDSubnetGroupA28971FC": {
      "Type": "AWS::RDS::DBSubnetGroup",
      "Properties": {
        "DBSubnetGroupDescription": "Subnet group for RDSBACKEND database",
        "SubnetIds": [
          {
            "Ref": "DEFAULTVPCPrivateSubnet1SubnetF3907A35"
          },
          {
            "Ref": "DEFAULTVPCPrivateSubnet2Subnet1F8B1A7D"
          }
        ]
      },
      "Metadata": {
        "aws:cdk:path": "MAINSTACK/RDSBACKEND/SubnetGroup"
      }
    },
    "RDSBACKENDSecurityGroup9B1EC05E": {
      "Type": "AWS::EC2::SecurityGroup",
      "Properties": {
        "GroupDescription": "Security group for RDSBACKEND database",
        "SecurityGroupEgress": [
          {
            "CidrIp": "0.0.0.0/0",
            "Description": "Allow all outbound traffic by default",
            "IpProtocol": "-1"
          }
        ],
        "VpcId": {
          "Ref": "DEFAULTVPCCF30E75C"
        }
      },
      "Metadata": {
        "aws:cdk:path": "MAINSTACK/RDSBACKEND/SecurityGroup/Resource"
      }
    },
    "RDSBACKENDSecretA61517F2": {
      "Type": "AWS::SecretsManager::Secret",
      "Properties": {
        "Description": {
          "Fn::Join": [
            "",
            [
              "Generated by the CDK for stack: ",
              {
                "Ref": "AWS::StackName"
              }
            ]
          ]
        },
        "GenerateSecretString": {
          "ExcludeCharacters": "\"@/\\",
          "GenerateStringKey": "password",
          "PasswordLength": 30,
          "SecretStringTemplate": "{\"username\":\"root\"}"
        }
      },
      "Metadata": {
        "aws:cdk:path": "MAINSTACK/RDSBACKEND/Secret/Resource"
      }
    },
    "RDSBACKENDSecretAttachment23E1EFEB": {
      "Type": "AWS::SecretsManager::SecretTargetAttachment",
      "Properties": {
        "SecretId": {
          "Ref": "RDSBACKENDSecretA61517F2"
        },
        "TargetId": {
          "Ref": "RDSBACKEND802020D5"
        },
        "TargetType": "AWS::RDS::DBInstance"
      },
      "Metadata": {
        "aws:cdk:path": "MAINSTACK/RDSBACKEND/Secret/Attachment/Resource"
      }
    },
    "RDSBACKEND802020D5": {
      "Type": "AWS::RDS::DBInstance",
      "Properties": {
        "DBInstanceClass": "db.m5.large",
        "AllocatedStorage": "100",
        "CopyTagsToSnapshot": true,
        "DBName": "mysqlMainDB",
        "DBSubnetGroupName": {
          "Ref": "RDSBACKENDSubnetGroupA28971FC"
        },
        "DeleteAutomatedBackups": true,
        "DeletionProtection": true,
        "Engine": "mysql",
        "MasterUsername": {
          "Fn::Join": [
            "",
            [
              "{{resolve:secretsmanager:",
              {
                "Ref": "RDSBACKENDSecretA61517F2"
              },
              ":SecretString:username::}}"
            ]
          ]
        },
        "MasterUserPassword": {
          "Fn::Join": [
            "",
            [
              "{{resolve:secretsmanager:",
              {
                "Ref": "RDSBACKENDSecretA61517F2"
              },
              ":SecretString:password::}}"
            ]
          ]
        },
        "MultiAZ": true,
        "Port": "3306",
        "StorageType": "gp2",
        "VPCSecurityGroups": [
          {
            "Fn::GetAtt": [
              "RDSBACKENDSecurityGroup9B1EC05E",
              "GroupId"
            ]
          }
        ]
      },
      "UpdateReplacePolicy": "Snapshot",
      "Metadata": {
        "aws:cdk:path": "MAINSTACK/RDSBACKEND/Resource"
      }
    }
  },
  "Parameters": {
    "SsmParameterValueawsserviceamiamazonlinuxlatestamznamihvmx8664gp2C96584B6F00A464EAD1953AFF4B05118Parameter": {
      "Type": "AWS::SSM::Parameter::Value<AWS::EC2::Image::Id>",
      "Default": "/aws/service/ami-amazon-linux-latest/amzn-ami-hvm-x86_64-gp2"
    }
  },
  "Outputs": {
    "RESTAPIEndpoint694760FB": {
      "Value": {
        "Fn::Join": [
          "",
          [
            "https://",
            {
              "Ref": "RESTAPIF36BC7AE"
            },
            ".execute-api.us-east-1.",
            {
              "Ref": "AWS::URLSuffix"
            },
            "/",
            {
              "Ref": "RESTAPIDeploymentStageprod63DE3AD3"
            },
            "/"
          ]
        ]
      }
    }
  }
}

```
