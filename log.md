2026-06-03T23:50:19.478Z
INIT_START Runtime Version: python:3.13.mainlinev2.v11 Runtime Version ARN: arn:aws:lambda:us-east-1::runtime:b80aa8cfc4306316d8164ccc5e4a7effaf5d6038865946d200964f23367ef28b
2026-06-03T23:50:19.575Z
[WARNING] 2026-06-03T23:50:19.575Z LAMBDA_WARNING: Unhandled exception. The most likely cause is an issue in the function code. However, in rare cases, a Lambda runtime update can cause unexpected function behavior. For functions using managed runtimes, runtime updates can be triggered by a function change, or can be applied automatically. To determine if the runtime has been updated, check the runtime version in the INIT_START log entry. If this error correlates with a change in the runtime version, you may be able to mitigate this error by temporarily rolling back to the previous runtime version. For more information, see https://docs.aws.amazon.com/lambda/latest/dg/runtimes-update.html
2026-06-03T23:50:19.575Z
[ERROR] Runtime.ImportModuleError: Unable to import module 'main': No module named 'main' Traceback (most recent call last):
2026-06-03T23:50:19.623Z
INIT_REPORT Init Duration: 144.81 ms Phase: init Status: error Error Type: Runtime.ImportModuleError
2026-06-03T23:50:19.689Z
[WARNING] 2026-06-03T23:50:19.689Z LAMBDA_WARNING: Unhandled exception. The most likely cause is an issue in the function code. However, in rare cases, a Lambda runtime update can cause unexpected function behavior. For functions using managed runtimes, runtime updates can be triggered by a function change, or can be applied automatically. To determine if the runtime has been updated, check the runtime version in the INIT_START log entry. If this error correlates with a change in the runtime version, you may be able to mitigate this error by temporarily rolling back to the previous runtime version. For more information, see https://docs.aws.amazon.com/lambda/latest/dg/runtimes-update.html
2026-06-03T23:50:19.689Z
[ERROR] Runtime.ImportModuleError: Unable to import module 'main': No module named 'main' Traceback (most recent call last):
2026-06-03T23:50:19.723Z
INIT_REPORT Init Duration: 88.26 ms Phase: invoke Status: error Error Type: Runtime.ImportModuleError
2026-06-03T23:50:19.723Z
START RequestId: da662309-f5c8-47ac-bbaa-89389a415df6 Version: $LATEST
2026-06-03T23:50:19.726Z
END RequestId: da662309-f5c8-47ac-bbaa-89389a415df6
2026-06-03T23:50:19.727Z
REPORT RequestId: da662309-f5c8-47ac-bbaa-89389a415df6 Duration: 97.66 ms B
