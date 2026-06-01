#plan


OpenTofu will perform the following actions:

  # aws_rds_cluster.aurora will be updated in-place
  ~ resource "aws_rds_cluster" "aurora" {
      ~ engine_version                        = "17.7" -> "17.4"
        id                                    = "realtimeinsurance-dev-aurora-cluster"
      ~ master_password_wo                    = (write-only attribute)
        tags                                  = {
            "Name" = "realtimeinsurance-dev-aurora-cluster"
        }
        # (46 unchanged attributes hidden)

        # (1 unchanged block hidden)
    }

  # aws_rds_cluster_instance.reader[0] will be updated in-place
  ~ resource "aws_rds_cluster_instance" "reader" {
      ~ engine_version                        = "17.7" -> "17.4"
        id                                    = "realtimeinsurance-dev-aurora-cluster-reader-1"
        tags                                  = {
            "Name" = "realtimeinsurance-dev-aurora-cluster-reader-1"
        }
        # (29 unchanged attributes hidden)
    }

  # aws_rds_cluster_instance.writer will be updated in-place
  ~ resource "aws_rds_cluster_instance" "writer" {
      ~ engine_version                        = "17.7" -> "17.4"
        id                                    = "realtimeinsurance-dev-aurora-cluster-writer"
        tags                                  = {
            "Name" = "realtimeinsurance-dev-aurora-cluster-writer"
        }
        # (29 unchanged attributes hidden)
    }

  # module.sample_lambda.aws_iam_role.this will be created
  + resource "aws_iam_role" "this" {
      + arn                   = (known after apply)
      + assume_role_policy    = jsonencode(
            {
              + Statement = [
                  + {
                      + Action    = "sts:AssumeRole"
                      + Effect    = "Allow"
                      + Principal = {
                          + Service = "lambda.amazonaws.com"
                        }
                    },
                ]
              + Version   = "2012-10-17"
            }
        )
      + create_date           = (known after apply)
      + force_detach_policies = false
      + id                    = (known after apply)
      + managed_policy_arns   = (known after apply)
      + max_session_duration  = 3600
      + name                  = "realtimeinsurance-dev-sample-lambda-role"
      + name_prefix           = (known after apply)
      + path                  = "/"
      + tags_all              = {
          + "application_name"      = "realtimeinsurance"
          + "business_ops_category" = "POL"
          + "created_by"            = "PlatformEngineering@kyfb.com"
          + "owned_by"              = "CloudOps@kyfb.com"
          + "requested_by"          = "PMOGroup@kyfb.com"
          + "source"                = "github.com/kfbmic/real-time-insurance-infra"
          + "terraform"             = "true"
        }
      + unique_id             = (known after apply)

      + inline_policy (known after apply)
    }

  # module.sample_lambda.aws_iam_role_policy.vpc_networking[0] will be created
  + resource "aws_iam_role_policy" "vpc_networking" {
      + id          = (known after apply)
      + name        = "realtimeinsurance-dev-sample-lambda-vpc-networking"
      + name_prefix = (known after apply)
      + policy      = jsonencode(
            {
              + Statement = [
                  + {
                      + Action   = [
                          + "ec2:CreateNetworkInterface",
                          + "ec2:DescribeNetworkInterfaces",
                          + "ec2:DeleteNetworkInterface",
                          + "ec2:AssignPrivateIpAddresses",
                          + "ec2:UnassignPrivateIpAddresses",
                          + "ec2:DescribeSubnets",
                          + "ec2:DescribeSecurityGroups",
                          + "ec2:DescribeVpcs",
                        ]
                      + Effect   = "Allow"
                      + Resource = "*"
                    },
                ]
              + Version   = "2012-10-17"
            }
        )
      + role        = (known after apply)
    }

  # module.sample_lambda.aws_iam_role_policy_attachment.basic_execution will be created
  + resource "aws_iam_role_policy_attachment" "basic_execution" {
      + id         = (known after apply)
      + policy_arn = "arn:aws:iam::aws:policy/service-role/AWSLambdaBasicExecutionRole"
      + role       = "realtimeinsurance-dev-sample-lambda-role"
    }

  # module.sample_lambda.aws_lambda_function.placeholder[0] will be created
  + resource "aws_lambda_function" "placeholder" {
      + architectures                  = [
          + "x86_64",
        ]
      + arn                            = (known after apply)
      + code_sha256                    = (known after apply)
      + filename                       = ".terraform/modules/sample_lambda/.build/realtimeinsurance-dev-sample-lambda-placeholder.zip"
      + function_name                  = "realtimeinsurance-dev-sample-lambda"
      + handler                        = "index.handler"
      + id                             = (known after apply)
      + invoke_arn                     = (known after apply)
      + last_modified                  = (known after apply)
      + memory_size                    = 128
      + package_type                   = "Zip"
      + publish                        = false
      + qualified_arn                  = (known after apply)
      + qualified_invoke_arn           = (known after apply)
      + region                         = "us-east-1"
      + reserved_concurrent_executions = -1
      + response_streaming_invoke_arn  = (known after apply)
      + role                           = (known after apply)
      + runtime                        = "python3.13"
      + signing_job_arn                = (known after apply)
      + signing_profile_version_arn    = (known after apply)
      + skip_destroy                   = false
      + source_code_hash               = "S/iyBXqejc2LD/9cNr4igEki2H2Kh5C82QME8jLIlCA="
      + source_code_size               = (known after apply)
      + tags_all                       = {
          + "application_name"      = "realtimeinsurance"
          + "business_ops_category" = "POL"
          + "created_by"            = "PlatformEngineering@kyfb.com"
          + "owned_by"              = "CloudOps@kyfb.com"
          + "requested_by"          = "PMOGroup@kyfb.com"
          + "source"                = "github.com/kfbmic/real-time-insurance-infra"
          + "terraform"             = "true"
        }
      + timeout                        = 10
      + version                        = (known after apply)

      + ephemeral_storage (known after apply)

      + logging_config (known after apply)

      + tracing_config (known after apply)

      + vpc_config {
          + ipv6_allowed_for_dual_stack = false
          + security_group_ids          = (known after apply)
          + subnet_ids                  = [
              + "subnet-0af508befdea0ef9f",
            ]
          + vpc_id                      = (known after apply)
        }
    }

  # module.sample_lambda.aws_security_group.this[0] will be created
  + resource "aws_security_group" "this" {
      + arn                    = (known after apply)
      + description            = "Security group for Lambda realtimeinsurance-dev-sample-lambda (no ingress; allow all egress)"
      + egress                 = [
          + {
              + cidr_blocks      = [
                  + "0.0.0.0/0",
                ]
              + description      = "Allow all egress IPv4"
              + from_port        = 0
              + ipv6_cidr_blocks = []
              + prefix_list_ids  = []
              + protocol         = "-1"
              + security_groups  = []
              + self             = false
              + to_port          = 0
            },
        ]
      + id                     = (known after apply)
      + ingress                = []
      + name                   = "realtimeinsurance-dev-sample-lambda-sg"
      + name_prefix            = (known after apply)
      + owner_id               = (known after apply)
      + region                 = "us-east-1"
      + revoke_rules_on_delete = false
      + tags_all               = {
          + "application_name"      = "realtimeinsurance"
          + "business_ops_category" = "POL"
          + "created_by"            = "PlatformEngineering@kyfb.com"
          + "owned_by"              = "CloudOps@kyfb.com"
          + "requested_by"          = "PMOGroup@kyfb.com"
          + "source"                = "github.com/kfbmic/real-time-insurance-infra"
          + "terraform"             = "true"
        }
      + vpc_id                 = "vpc-05b9da12fe9d64805"
    }

  # module.soap_api_gateway.aws_api_gateway_deployment.this must be replaced
-/+ resource "aws_api_gateway_deployment" "this" {
      ~ created_date = "2026-05-20T19:56:18Z" -> (known after apply)
      ~ id           = "eeqx3o" -> (known after apply)
      ~ triggers     = { # forces replacement
          - "redeploy" = "77488d4d7ffd3b8dea623ef7ae76f349674a766b"
        } -> (known after apply) # forces replacement
        # (2 unchanged attributes hidden)
    }

  # module.soap_api_gateway.aws_api_gateway_integration.this["GET /soap"] will be updated in-place
  ~ resource "aws_api_gateway_integration" "this" {
        id                      = "agi-q51dqcsrw5-lknkms-GET"
      ~ uri                     = "arn:aws:apigateway:us-east-1:lambda:path/2015-03-31/functions/arn:aws:lambda:us-east-1:058264370150:function:realtimeinsurance-dev-soap-verification-lambda/invocations" -> (known after apply)
        # (14 unchanged attributes hidden)
    }

  # module.soap_api_gateway.aws_api_gateway_rest_api.this will be updated in-place
  ~ resource "aws_api_gateway_rest_api" "this" {
        id                           = "q51dqcsrw5"
        name                         = "realtimeinsurance-dev-soap-api-gateway"
      ~ policy                       = jsonencode(
          ~ {
              ~ Statement = [
                  ~ {
                      ~ Condition = {
                          ~ NotIpAddress = {
                              ~ "aws:SourceIp" = [
                                    # (2 unchanged elements hidden)
                                    "198.51.100.5/32",
                                  + "10.214.100.255/32",
                                ]
                            }
                        }
                        # (5 unchanged attributes hidden)
                    },
                    {
                        Action    = "execute-api:Invoke"
                        Effect    = "Allow"
                        Principal = "*"
                        Resource  = "arn:aws:execute-api:us-east-1:058264370150:*/*/*/*"
                        Sid       = "AllowInvoke"
                    },
                ]
                # (1 unchanged attribute hidden)
            }
        )
        tags                         = {}
        # (9 unchanged attributes hidden)

        # (1 unchanged block hidden)
    }

  # module.soap_api_gateway.aws_api_gateway_stage.this will be updated in-place
  ~ resource "aws_api_gateway_stage" "this" {
      ~ deployment_id         = "xltaio" -> (known after apply)
        id                    = "ags-q51dqcsrw5-default"
        tags                  = {}
        # (10 unchanged attributes hidden)
    }

  # module.soap_api_gateway.aws_lambda_permission.allow_apigw_invoke_backend["GET /soap"] will be created
  + resource "aws_lambda_permission" "allow_apigw_invoke_backend" {
      + action              = "lambda:InvokeFunction"
      + function_name       = (known after apply)
      + id                  = (known after apply)
      + principal           = "apigateway.amazonaws.com"
      + region              = "us-east-1"
      + source_arn          = "arn:aws:execute-api:us-east-1:058264370150:q51dqcsrw5/*/GET/soap"
      + statement_id        = "AllowAPIGatewayInvoke-GET__soap"
      + statement_id_prefix = (known after apply)
    }

  # module.soap_verification_lambda.aws_iam_role.this will be destroyed
  # (because aws_iam_role.this is not in configuration)
  - resource "aws_iam_role" "this" {
      - arn                   = "arn:aws:iam::058264370150:role/realtimeinsurance-dev-soap-verification-lambda-role" -> null
      - assume_role_policy    = jsonencode(
            {
              - Statement = [
                  - {
                      - Action    = "sts:AssumeRole"
                      - Effect    = "Allow"
                      - Principal = {
                          - Service = "lambda.amazonaws.com"
                        }
                    },
                ]
              - Version   = "2012-10-17"
            }
        ) -> null
      - create_date           = "2026-05-20T19:50:24Z" -> null
      - force_detach_policies = false -> null
      - id                    = "realtimeinsurance-dev-soap-verification-lambda-role" -> null
      - managed_policy_arns   = [] -> null
      - max_session_duration  = 3600 -> null
      - name                  = "realtimeinsurance-dev-soap-verification-lambda-role" -> null
      - path                  = "/" -> null
      - tags                  = {} -> null
      - tags_all              = {
          - "application_name"      = "realtimeinsurance"
          - "business_ops_category" = "POL"
          - "created_by"            = "PlatformEngineering@kyfb.com"
          - "owned_by"              = "CloudOps@kyfb.com"
          - "requested_by"          = "PMOGroup@kyfb.com"
          - "source"                = "github.com/kfbmic/real-time-insurance-infra"
          - "terraform"             = "true"
        } -> null
      - unique_id             = "AROAQ3EGTXPTPQOIY2QDP" -> null
    }

  # module.soap_verification_lambda.aws_lambda_function.placeholder[0] will be destroyed
  # (because aws_lambda_function.placeholder is not in configuration)
  - resource "aws_lambda_function" "placeholder" {
      - architectures                  = [
          - "x86_64",
        ] -> null
      - arn                            = "arn:aws:lambda:us-east-1:058264370150:function:realtimeinsurance-dev-soap-verification-lambda" -> null
      - code_sha256                    = "B8PuG11h5OJHTn482WhGtg8RU6dzZWaKzz1gEfAbgls=" -> null
      - filename                       = ".terraform/modules/soap_verification_lambda/.build/realtimeinsurance-dev-soap-verification-lambda-placeholder.zip" -> null
      - function_name                  = "realtimeinsurance-dev-soap-verification-lambda" -> null
      - handler                        = "main.lambda_handler" -> null
      - id                             = "realtimeinsurance-dev-soap-verification-lambda" -> null
      - invoke_arn                     = "arn:aws:apigateway:us-east-1:lambda:path/2015-03-31/functions/arn:aws:lambda:us-east-1:058264370150:function:realtimeinsurance-dev-soap-verification-lambda/invocations" -> null
      - last_modified                  = "2026-05-26T16:45:29.000+0000" -> null
      - layers                         = [] -> null
      - memory_size                    = 128 -> null
      - package_type                   = "Zip" -> null
      - publish                        = false -> null
      - qualified_arn                  = "arn:aws:lambda:us-east-1:058264370150:function:realtimeinsurance-dev-soap-verification-lambda:$LATEST" -> null
      - qualified_invoke_arn           = "arn:aws:apigateway:us-east-1:lambda:path/2015-03-31/functions/arn:aws:lambda:us-east-1:058264370150:function:realtimeinsurance-dev-soap-verification-lambda:$LATEST/invocations" -> null
      - region                         = "us-east-1" -> null
      - reserved_concurrent_executions = -1 -> null
      - response_streaming_invoke_arn  = "arn:aws:apigateway:us-east-1:lambda:path/2021-11-15/functions/arn:aws:lambda:us-east-1:058264370150:function:realtimeinsurance-dev-soap-verification-lambda/response-streaming-invocations" -> null
      - role                           = "arn:aws:iam::058264370150:role/realtimeinsurance-dev-soap-verification-lambda-role" -> null
      - runtime                        = "python3.13" -> null
      - skip_destroy                   = false -> null
      - source_code_hash               = "S/iyBXqejc2LD/9cNr4igEki2H2Kh5C82QME8jLIlCA=" -> null
      - source_code_size               = 17489136 -> null
      - tags                           = {} -> null
      - tags_all                       = {
          - "application_name"      = "realtimeinsurance"
          - "business_ops_category" = "POL"
          - "created_by"            = "PlatformEngineering@kyfb.com"
          - "owned_by"              = "CloudOps@kyfb.com"
          - "requested_by"          = "PMOGroup@kyfb.com"
          - "source"                = "github.com/kfbmic/real-time-insurance-infra"
          - "terraform"             = "true"
        } -> null
      - timeout                        = 10 -> null
      - version                        = "$LATEST" -> null

      - environment {
          - variables = {
              - "db_endpoint" = "realtimeinsurance-dev-aurora-cluster.cluster-ro-cx08iswmk3mr.us-east-1.rds.amazonaws.com"
              - "db_name"     = "realtimeinsurance_dev"
              - "db_region"   = "us-east-1"
              - "db_user"     = "lambda_svc"
            } -> null
        }

      - ephemeral_storage {
          - size = 512 -> null
        }

      - logging_config {
          - log_format = "Text" -> null
          - log_group  = "/aws/lambda/realtimeinsurance-dev-soap-verification-lambda" -> null
        }

      - tracing_config {
          - mode = "PassThrough" -> null
        }

      - vpc_config {
          - ipv6_allowed_for_dual_stack = false -> null
          - security_group_ids          = [
              - "sg-04d42cff2e98a040b",
            ] -> null
          - subnet_ids                  = [
              - "subnet-0af508befdea0ef9f",
            ] -> null
          - vpc_id                      = "vpc-05b9da12fe9d64805" -> null
        }
    }

  # module.soap_verification_lambda.aws_security_group.this[0] will be destroyed
  # (because aws_security_group.this is not in configuration)
  - resource "aws_security_group" "this" {
      - arn                    = "arn:aws:ec2:us-east-1:058264370150:security-group/sg-04d42cff2e98a040b" -> null
      - description            = "Security group for Lambda realtimeinsurance-dev-soap-verification-lambda (no ingress; allow all egress)" -> null
      - egress                 = [
          - {
              - cidr_blocks      = [
                  - "0.0.0.0/0",
                ]
              - description      = "Allow all egress IPv4"
              - from_port        = 0
              - ipv6_cidr_blocks = []
              - prefix_list_ids  = []
              - protocol         = "-1"
              - security_groups  = []
              - self             = false
              - to_port          = 0
            },
        ] -> null
      - id                     = "sg-04d42cff2e98a040b" -> null
      - ingress                = [] -> null
      - name                   = "realtimeinsurance-dev-soap-verification-lambda-sg" -> null
      - owner_id               = "058264370150" -> null
      - region                 = "us-east-1" -> null
      - revoke_rules_on_delete = false -> null
      - tags                   = {} -> null
      - tags_all               = {
          - "application_name"      = "realtimeinsurance"
          - "business_ops_category" = "POL"
          - "created_by"            = "PlatformEngineering@kyfb.com"
          - "owned_by"              = "CloudOps@kyfb.com"
          - "requested_by"          = "PMOGroup@kyfb.com"
          - "source"                = "github.com/kfbmic/real-time-insurance-infra"
          - "terraform"             = "true"
        } -> null
      - vpc_id                 = "vpc-05b9da12fe9d64805" -> null
    }

Plan: 7 to add, 6 to change, 4 to destroy.




#Apply

OpenTofu will perform the following actions:

  # aws_rds_cluster.aurora will be updated in-place
  ~ resource "aws_rds_cluster" "aurora" {
      ~ engine_version                        = "17.7" -> "17.4"
        id                                    = "realtimeinsurance-dev-aurora-cluster"
      ~ master_password_wo                    = (write-only attribute)
        tags                                  = {
            "Name" = "realtimeinsurance-dev-aurora-cluster"
        }
        # (46 unchanged attributes hidden)

        # (1 unchanged block hidden)
    }

  # aws_rds_cluster_instance.reader[0] will be updated in-place
  ~ resource "aws_rds_cluster_instance" "reader" {
      ~ engine_version                        = "17.7" -> "17.4"
        id                                    = "realtimeinsurance-dev-aurora-cluster-reader-1"
        tags                                  = {
            "Name" = "realtimeinsurance-dev-aurora-cluster-reader-1"
        }
        # (29 unchanged attributes hidden)
    }

  # aws_rds_cluster_instance.writer will be updated in-place
  ~ resource "aws_rds_cluster_instance" "writer" {
      ~ engine_version                        = "17.7" -> "17.4"
        id                                    = "realtimeinsurance-dev-aurora-cluster-writer"
        tags                                  = {
            "Name" = "realtimeinsurance-dev-aurora-cluster-writer"
        }
        # (29 unchanged attributes hidden)
    }

  # module.sample_lambda.aws_iam_role.this will be created
  + resource "aws_iam_role" "this" {
      + arn                   = (known after apply)
      + assume_role_policy    = jsonencode(
            {
              + Statement = [
                  + {
                      + Action    = "sts:AssumeRole"
                      + Effect    = "Allow"
                      + Principal = {
                          + Service = "lambda.amazonaws.com"
                        }
                    },
                ]
              + Version   = "2012-10-17"
            }
        )
      + create_date           = (known after apply)
      + force_detach_policies = false
      + id                    = (known after apply)
      + managed_policy_arns   = (known after apply)
      + max_session_duration  = 3600
      + name                  = "realtimeinsurance-dev-sample-lambda-role"
      + name_prefix           = (known after apply)
      + path                  = "/"
      + tags_all              = {
          + "application_name"      = "realtimeinsurance"
          + "business_ops_category" = "POL"
          + "created_by"            = "PlatformEngineering@kyfb.com"
          + "owned_by"              = "CloudOps@kyfb.com"
          + "requested_by"          = "PMOGroup@kyfb.com"
          + "source"                = "github.com/kfbmic/real-time-insurance-infra"
          + "terraform"             = "true"
        }
      + unique_id             = (known after apply)

      + inline_policy (known after apply)
    }

  # module.sample_lambda.aws_iam_role_policy.vpc_networking[0] will be created
  + resource "aws_iam_role_policy" "vpc_networking" {
      + id          = (known after apply)
      + name        = "realtimeinsurance-dev-sample-lambda-vpc-networking"
      + name_prefix = (known after apply)
      + policy      = jsonencode(
            {
              + Statement = [
                  + {
                      + Action   = [
                          + "ec2:CreateNetworkInterface",
                          + "ec2:DescribeNetworkInterfaces",
                          + "ec2:DeleteNetworkInterface",
                          + "ec2:AssignPrivateIpAddresses",
                          + "ec2:UnassignPrivateIpAddresses",
                          + "ec2:DescribeSubnets",
                          + "ec2:DescribeSecurityGroups",
                          + "ec2:DescribeVpcs",
                        ]
                      + Effect   = "Allow"
                      + Resource = "*"
                    },
                ]
              + Version   = "2012-10-17"
            }
        )
      + role        = (known after apply)
    }

  # module.sample_lambda.aws_iam_role_policy_attachment.basic_execution will be created
  + resource "aws_iam_role_policy_attachment" "basic_execution" {
      + id         = (known after apply)
      + policy_arn = "arn:aws:iam::aws:policy/service-role/AWSLambdaBasicExecutionRole"
      + role       = "realtimeinsurance-dev-sample-lambda-role"
    }

  # module.sample_lambda.aws_lambda_function.placeholder[0] will be created
  + resource "aws_lambda_function" "placeholder" {
      + architectures                  = [
          + "x86_64",
        ]
      + arn                            = (known after apply)
      + code_sha256                    = (known after apply)
      + filename                       = ".terraform/modules/sample_lambda/.build/realtimeinsurance-dev-sample-lambda-placeholder.zip"
      + function_name                  = "realtimeinsurance-dev-sample-lambda"
      + handler                        = "index.handler"
      + id                             = (known after apply)
      + invoke_arn                     = (known after apply)
      + last_modified                  = (known after apply)
      + memory_size                    = 128
      + package_type                   = "Zip"
      + publish                        = false
      + qualified_arn                  = (known after apply)
      + qualified_invoke_arn           = (known after apply)
      + region                         = "us-east-1"
      + reserved_concurrent_executions = -1
      + response_streaming_invoke_arn  = (known after apply)
      + role                           = (known after apply)
      + runtime                        = "python3.13"
      + signing_job_arn                = (known after apply)
      + signing_profile_version_arn    = (known after apply)
      + skip_destroy                   = false
      + source_code_hash               = "S/iyBXqejc2LD/9cNr4igEki2H2Kh5C82QME8jLIlCA="
      + source_code_size               = (known after apply)
      + tags_all                       = {
          + "application_name"      = "realtimeinsurance"
          + "business_ops_category" = "POL"
          + "created_by"            = "PlatformEngineering@kyfb.com"
          + "owned_by"              = "CloudOps@kyfb.com"
          + "requested_by"          = "PMOGroup@kyfb.com"
          + "source"                = "github.com/kfbmic/real-time-insurance-infra"
          + "terraform"             = "true"
        }
      + timeout                        = 10
      + version                        = (known after apply)

      + ephemeral_storage (known after apply)

      + logging_config (known after apply)

      + tracing_config (known after apply)

      + vpc_config {
          + ipv6_allowed_for_dual_stack = false
          + security_group_ids          = (known after apply)
          + subnet_ids                  = [
              + "subnet-0af508befdea0ef9f",
            ]
          + vpc_id                      = (known after apply)
        }
    }

  # module.sample_lambda.aws_security_group.this[0] will be created
  + resource "aws_security_group" "this" {
      + arn                    = (known after apply)
      + description            = "Security group for Lambda realtimeinsurance-dev-sample-lambda (no ingress; allow all egress)"
      + egress                 = [
          + {
              + cidr_blocks      = [
                  + "0.0.0.0/0",
                ]
              + description      = "Allow all egress IPv4"
              + from_port        = 0
              + ipv6_cidr_blocks = []
              + prefix_list_ids  = []
              + protocol         = "-1"
              + security_groups  = []
              + self             = false
              + to_port          = 0
            },
        ]
      + id                     = (known after apply)
      + ingress                = []
      + name                   = "realtimeinsurance-dev-sample-lambda-sg"
      + name_prefix            = (known after apply)
      + owner_id               = (known after apply)
      + region                 = "us-east-1"
      + revoke_rules_on_delete = false
      + tags_all               = {
          + "application_name"      = "realtimeinsurance"
          + "business_ops_category" = "POL"
          + "created_by"            = "PlatformEngineering@kyfb.com"
          + "owned_by"              = "CloudOps@kyfb.com"
          + "requested_by"          = "PMOGroup@kyfb.com"
          + "source"                = "github.com/kfbmic/real-time-insurance-infra"
          + "terraform"             = "true"
        }
      + vpc_id                 = "vpc-05b9da12fe9d64805"
    }

  # module.soap_api_gateway.aws_api_gateway_deployment.this must be replaced
-/+ resource "aws_api_gateway_deployment" "this" {
      ~ created_date = "2026-05-20T19:56:18Z" -> (known after apply)
      ~ id           = "eeqx3o" -> (known after apply)
      ~ triggers     = { # forces replacement
          - "redeploy" = "77488d4d7ffd3b8dea623ef7ae76f349674a766b"
        } -> (known after apply) # forces replacement
        # (2 unchanged attributes hidden)
    }

  # module.soap_api_gateway.aws_api_gateway_domain_name.this[0] will be updated in-place
  ~ resource "aws_api_gateway_domain_name" "this" {
        id                       = "realtimeinsurance-soap-api-dev.devkyfb.com"
        tags                     = {}
        # (11 unchanged attributes hidden)

      - mutual_tls_authentication {
          - truststore_uri = "s3://realtimeinsurance-dev-soap-api-truststore/soap-truststore/truststore.pem" -> null
        }

        # (1 unchanged block hidden)
    }

  # module.soap_api_gateway.aws_api_gateway_integration.this["GET /soap"] will be updated in-place
  ~ resource "aws_api_gateway_integration" "this" {
        id                      = "agi-q51dqcsrw5-lknkms-GET"
      ~ uri                     = "arn:aws:apigateway:us-east-1:lambda:path/2015-03-31/functions/arn:aws:lambda:us-east-1:058264370150:function:realtimeinsurance-dev-soap-verification-lambda/invocations" -> (known after apply)
        # (14 unchanged attributes hidden)
    }

  # module.soap_api_gateway.aws_api_gateway_stage.this will be updated in-place
  ~ resource "aws_api_gateway_stage" "this" {
      ~ deployment_id         = "eeqx3o" -> (known after apply)
        id                    = "ags-q51dqcsrw5-default"
        tags                  = {}
        # (10 unchanged attributes hidden)
    }

  # module.soap_api_gateway.aws_lambda_permission.allow_apigw_invoke_backend["GET /soap"] will be created
  + resource "aws_lambda_permission" "allow_apigw_invoke_backend" {
      + action              = "lambda:InvokeFunction"
      + function_name       = (known after apply)
      + id                  = (known after apply)
      + principal           = "apigateway.amazonaws.com"
      + region              = "us-east-1"
      + source_arn          = "arn:aws:execute-api:us-east-1:058264370150:q51dqcsrw5/*/GET/soap"
      + statement_id        = "AllowAPIGatewayInvoke-GET__soap"
      + statement_id_prefix = (known after apply)
    }

  # module.soap_verification_lambda.aws_iam_role.this will be destroyed
  # (because aws_iam_role.this is not in configuration)
  - resource "aws_iam_role" "this" {
      - arn                   = "arn:aws:iam::058264370150:role/realtimeinsurance-dev-soap-verification-lambda-role" -> null
      - assume_role_policy    = jsonencode(
            {
              - Statement = [
                  - {
                      - Action    = "sts:AssumeRole"
                      - Effect    = "Allow"
                      - Principal = {
                          - Service = "lambda.amazonaws.com"
                        }
                    },
                ]
              - Version   = "2012-10-17"
            }
        ) -> null
      - create_date           = "2026-05-20T19:50:24Z" -> null
      - force_detach_policies = false -> null
      - id                    = "realtimeinsurance-dev-soap-verification-lambda-role" -> null
      - managed_policy_arns   = [] -> null
      - max_session_duration  = 3600 -> null
      - name                  = "realtimeinsurance-dev-soap-verification-lambda-role" -> null
      - path                  = "/" -> null
      - tags                  = {} -> null
      - tags_all              = {
          - "application_name"      = "realtimeinsurance"
          - "business_ops_category" = "POL"
          - "created_by"            = "PlatformEngineering@kyfb.com"
          - "owned_by"              = "CloudOps@kyfb.com"
          - "requested_by"          = "PMOGroup@kyfb.com"
          - "source"                = "github.com/kfbmic/real-time-insurance-infra"
          - "terraform"             = "true"
        } -> null
      - unique_id             = "AROAQ3EGTXPTPQOIY2QDP" -> null
    }

  # module.soap_verification_lambda.aws_lambda_function.placeholder[0] will be destroyed
  # (because aws_lambda_function.placeholder is not in configuration)
  - resource "aws_lambda_function" "placeholder" {
      - architectures                  = [
          - "x86_64",
        ] -> null
      - arn                            = "arn:aws:lambda:us-east-1:058264370150:function:realtimeinsurance-dev-soap-verification-lambda" -> null
      - code_sha256                    = "B8PuG11h5OJHTn482WhGtg8RU6dzZWaKzz1gEfAbgls=" -> null
      - filename                       = ".terraform/modules/soap_verification_lambda/.build/realtimeinsurance-dev-soap-verification-lambda-placeholder.zip" -> null
      - function_name                  = "realtimeinsurance-dev-soap-verification-lambda" -> null
      - handler                        = "main.lambda_handler" -> null
      - id                             = "realtimeinsurance-dev-soap-verification-lambda" -> null
      - invoke_arn                     = "arn:aws:apigateway:us-east-1:lambda:path/2015-03-31/functions/arn:aws:lambda:us-east-1:058264370150:function:realtimeinsurance-dev-soap-verification-lambda/invocations" -> null
      - last_modified                  = "2026-05-26T16:45:29.000+0000" -> null
      - layers                         = [] -> null
      - memory_size                    = 128 -> null
      - package_type                   = "Zip" -> null
      - publish                        = false -> null
      - qualified_arn                  = "arn:aws:lambda:us-east-1:058264370150:function:realtimeinsurance-dev-soap-verification-lambda:$LATEST" -> null
      - qualified_invoke_arn           = "arn:aws:apigateway:us-east-1:lambda:path/2015-03-31/functions/arn:aws:lambda:us-east-1:058264370150:function:realtimeinsurance-dev-soap-verification-lambda:$LATEST/invocations" -> null
      - region                         = "us-east-1" -> null
      - reserved_concurrent_executions = -1 -> null
      - response_streaming_invoke_arn  = "arn:aws:apigateway:us-east-1:lambda:path/2021-11-15/functions/arn:aws:lambda:us-east-1:058264370150:function:realtimeinsurance-dev-soap-verification-lambda/response-streaming-invocations" -> null
      - role                           = "arn:aws:iam::058264370150:role/realtimeinsurance-dev-soap-verification-lambda-role" -> null
      - runtime                        = "python3.13" -> null
      - skip_destroy                   = false -> null
      - source_code_hash               = "S/iyBXqejc2LD/9cNr4igEki2H2Kh5C82QME8jLIlCA=" -> null
      - source_code_size               = 17489136 -> null
      - tags                           = {} -> null
      - tags_all                       = {
          - "application_name"      = "realtimeinsurance"
          - "business_ops_category" = "POL"
          - "created_by"            = "PlatformEngineering@kyfb.com"
          - "owned_by"              = "CloudOps@kyfb.com"
          - "requested_by"          = "PMOGroup@kyfb.com"
          - "source"                = "github.com/kfbmic/real-time-insurance-infra"
          - "terraform"             = "true"
        } -> null
      - timeout                        = 10 -> null
      - version                        = "$LATEST" -> null

      - environment {
          - variables = {
              - "db_endpoint" = "realtimeinsurance-dev-aurora-cluster.cluster-ro-cx08iswmk3mr.us-east-1.rds.amazonaws.com"
              - "db_name"     = "realtimeinsurance_dev"
              - "db_region"   = "us-east-1"
              - "db_user"     = "lambda_svc"
            } -> null
        }

      - ephemeral_storage {
          - size = 512 -> null
        }

      - logging_config {
          - log_format = "Text" -> null
          - log_group  = "/aws/lambda/realtimeinsurance-dev-soap-verification-lambda" -> null
        }

      - tracing_config {
          - mode = "PassThrough" -> null
        }

      - vpc_config {
          - ipv6_allowed_for_dual_stack = false -> null
          - security_group_ids          = [
              - "sg-04d42cff2e98a040b",
            ] -> null
          - subnet_ids                  = [
              - "subnet-0af508befdea0ef9f",
            ] -> null
          - vpc_id                      = "vpc-05b9da12fe9d64805" -> null
        }
    }

  # module.soap_verification_lambda.aws_security_group.this[0] will be destroyed
  # (because aws_security_group.this is not in configuration)
  - resource "aws_security_group" "this" {
      - arn                    = "arn:aws:ec2:us-east-1:058264370150:security-group/sg-04d42cff2e98a040b" -> null
      - description            = "Security group for Lambda realtimeinsurance-dev-soap-verification-lambda (no ingress; allow all egress)" -> null
      - egress                 = [
          - {
              - cidr_blocks      = [
                  - "0.0.0.0/0",
                ]
              - description      = "Allow all egress IPv4"
              - from_port        = 0
              - ipv6_cidr_blocks = []
              - prefix_list_ids  = []
              - protocol         = "-1"
              - security_groups  = []
              - self             = false
              - to_port          = 0
            },
        ] -> null
      - id                     = "sg-04d42cff2e98a040b" -> null
      - ingress                = [] -> null
      - name                   = "realtimeinsurance-dev-soap-verification-lambda-sg" -> null
      - owner_id               = "058264370150" -> null
      - region                 = "us-east-1" -> null
      - revoke_rules_on_delete = false -> null
      - tags                   = {} -> null
      - tags_all               = {
          - "application_name"      = "realtimeinsurance"
          - "business_ops_category" = "POL"
          - "created_by"            = "PlatformEngineering@kyfb.com"
          - "owned_by"              = "CloudOps@kyfb.com"
          - "requested_by"          = "PMOGroup@kyfb.com"
          - "source"                = "github.com/kfbmic/real-time-insurance-infra"
          - "terraform"             = "true"
        } -> null
      - vpc_id                 = "vpc-05b9da12fe9d64805" -> null
    }

Plan: 7 to add, 6 to change, 4 to destroy.
module.soap_api_gateway.aws_api_gateway_deployment.this: Destroying... [id=eeqx3o]
module.soap_api_gateway.aws_api_gateway_domain_name.this[0]: Modifying... [id=realtimeinsurance-soap-api-dev.devkyfb.com]
module.soap_api_gateway.aws_api_gateway_domain_name.this[0]: Still modifying... [id=realtimeinsurance-soap-api-dev.devkyfb.com, 10s elapsed]
module.soap_api_gateway.aws_api_gateway_domain_name.this[0]: Still modifying... [id=realtimeinsurance-soap-api-dev.devkyfb.com, 20s elapsed]
module.soap_api_gateway.aws_api_gateway_domain_name.this[0]: Still modifying... [id=realtimeinsurance-soap-api-dev.devkyfb.com, 30s elapsed]
module.soap_api_gateway.aws_api_gateway_domain_name.this[0]: Still modifying... [id=realtimeinsurance-soap-api-dev.devkyfb.com, 40s elapsed]
module.soap_api_gateway.aws_api_gateway_domain_name.this[0]: Still modifying... [id=realtimeinsurance-soap-api-dev.devkyfb.com, 50s elapsed]
module.soap_api_gateway.aws_api_gateway_domain_name.this[0]: Still modifying... [id=realtimeinsurance-soap-api-dev.devkyfb.com, 1m0s elapsed]
module.soap_api_gateway.aws_api_gateway_domain_name.this[0]: Still modifying... [id=realtimeinsurance-soap-api-dev.devkyfb.com, 1m10s elapsed]
module.soap_api_gateway.aws_api_gateway_domain_name.this[0]: Still modifying... [id=realtimeinsurance-soap-api-dev.devkyfb.com, 1m20s elapsed]
module.soap_api_gateway.aws_api_gateway_domain_name.this[0]: Still modifying... [id=realtimeinsurance-soap-api-dev.devkyfb.com, 1m30s elapsed]
module.soap_api_gateway.aws_api_gateway_domain_name.this[0]: Still modifying... [id=realtimeinsurance-soap-api-dev.devkyfb.com, 1m40s elapsed]
module.soap_api_gateway.aws_api_gateway_domain_name.this[0]: Still modifying... [id=realtimeinsurance-soap-api-dev.devkyfb.com, 1m50s elapsed]
module.soap_api_gateway.aws_api_gateway_domain_name.this[0]: Still modifying... [id=realtimeinsurance-soap-api-dev.devkyfb.com, 2m0s elapsed]
module.soap_api_gateway.aws_api_gateway_domain_name.this[0]: Still modifying... [id=realtimeinsurance-soap-api-dev.devkyfb.com, 2m10s elapsed]
module.soap_api_gateway.aws_api_gateway_domain_name.this[0]: Still modifying... [id=realtimeinsurance-soap-api-dev.devkyfb.com, 2m20s elapsed]
module.soap_api_gateway.aws_api_gateway_domain_name.this[0]: Still modifying... [id=realtimeinsurance-soap-api-dev.devkyfb.com, 2m30s elapsed]
module.soap_api_gateway.aws_api_gateway_domain_name.this[0]: Still modifying... [id=realtimeinsurance-soap-api-dev.devkyfb.com, 2m40s elapsed]
module.soap_api_gateway.aws_api_gateway_domain_name.this[0]: Still modifying... [id=realtimeinsurance-soap-api-dev.devkyfb.com, 2m50s elapsed]
module.soap_api_gateway.aws_api_gateway_domain_name.this[0]: Still modifying... [id=realtimeinsurance-soap-api-dev.devkyfb.com, 3m0s elapsed]
module.soap_api_gateway.aws_api_gateway_domain_name.this[0]: Still modifying... [id=realtimeinsurance-soap-api-dev.devkyfb.com, 3m10s elapsed]
module.soap_api_gateway.aws_api_gateway_domain_name.this[0]: Still modifying... [id=realtimeinsurance-soap-api-dev.devkyfb.com, 3m20s elapsed]
module.soap_api_gateway.aws_api_gateway_domain_name.this[0]: Still modifying... [id=realtimeinsurance-soap-api-dev.devkyfb.com, 3m30s elapsed]
module.soap_api_gateway.aws_api_gateway_domain_name.this[0]: Still modifying... [id=realtimeinsurance-soap-api-dev.devkyfb.com, 3m40s elapsed]
module.soap_api_gateway.aws_api_gateway_domain_name.this[0]: Still modifying... [id=realtimeinsurance-soap-api-dev.devkyfb.com, 3m50s elapsed]
module.soap_api_gateway.aws_api_gateway_domain_name.this[0]: Still modifying... [id=realtimeinsurance-soap-api-dev.devkyfb.com, 4m0s elapsed]
module.soap_api_gateway.aws_api_gateway_domain_name.this[0]: Still modifying... [id=realtimeinsurance-soap-api-dev.devkyfb.com, 4m10s elapsed]
module.soap_api_gateway.aws_api_gateway_domain_name.this[0]: Modifications complete after 4m16s [id=realtimeinsurance-soap-api-dev.devkyfb.com]
╷
│ Warning: Value derived from a deprecated source
│ 
│   with module.api_gateway.aws_api_gateway_authorizer.jwt,
│   on .terraform/modules/api_gateway/main.tf line 177, in resource "aws_api_gateway_authorizer" "jwt":
│  177:   type            = "TOKEN"
│ 
│ This value is derived from data.aws_region.current.name, which is
│ deprecated with the following message:
│ 
│ name is deprecated. Use region instead.
╵
╷
│ Warning: Redundant ignore_changes element
│ 
╷
│ Error: deleting API Gateway Deployment (eeqx3o): operation error API Gateway: DeleteDeployment, https response error StatusCode: 400, RequestID: 9566d54d-13f8-4b2f-9077-1e9244c114b8, BadRequestException: Active stages pointing to this deployment must be moved or deleted
│ 
│   on .terraform/modules/hello_lambda/main.tf line 152, in resource "aws_lambda_function" "placeholder":
│ 
│  152: resource "aws_lambda_function" "placeholder" {
╵
│ 
│ Adding an attribute name to ignore_changes tells OpenTofu to ignore future
│ changes to the argument in configuration after the object has been created,
│ retaining the value originally configured.
│ 
│ The attribute last_modified is decided by the provider alone and therefore
│ there can be no configured value to compare with. Including this attribute
│ in ignore_changes has no effect. Remove the attribute from ignore_changes
│ to quiet this warning.
│ 
│ (and 5 more similar warnings elsewhere)
╵
Error: OpenTofu exited with code 1.
Error: Process completed with exit code 1.
