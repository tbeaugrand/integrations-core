# Gitlab Runner Integration

## Overview

Integration that allows to:

* Visualize and monitor metrics collected via Gitlab Runners through Prometheus
* Validate that the Gitlab Runner can connect to Gitlab

See https://docs.gitlab.com/runner/monitoring/README.html for
more information about Gitlab Runner and its integration with Prometheus

## Setup
### Installation

The Gitlab Runner check is packaged with the Agent, so simply [install the Agent](https://app.datadoghq.com/account/settings#agent) on your Gitlab servers.  

If you need the newest version of the Gitlab Runner check, install the `dd-check-gitlab_runner` package; this package's check overrides the one packaged with the Agent. See the [integrations-core repository README.md for more details](https://github.com/DataDog/integrations-core#installing-the-integrations).

### Configuration

Edit the `gitlab_runner.yaml` file to point to the Runner's Prometheus metrics endpoint and to the Gitlab master to have a service check.
See the [sample gitlab_runner.yaml](https://github.com/DataDog/integrations-core/blob/master/gitlab_runner/conf.yaml.example) for all available configuration options.

The `allowed_metrics` item in the `init_config` section allows to specify the metrics that should be extracted.

**Remarks:**

 - Some metrics should be reported as `rate` (i.e., `ci_runner_errors`)


### Validation

[Run the Agent's `info` subcommand](https://docs.datadoghq.com/agent/faq/agent-status-and-information/) and look for `gitlab_runner` under the Checks section:

    Checks
    ======

        gitlab_runner
        -----------
          - instance #0 [OK]
          - Collected 10 metrics, 0 events & 2 service checks

## Compatibility

The gitlab_runner check is compatible with all major platforms

## Data Collected
### Metrics
See [metadata.csv](https://github.com/DataDog/integrations-core/blob/master/gitlab_runner/metadata.csv) for a list of metrics provided by this integration.

### Events
The Gitlab Runner check does not include any event at this time.

### Service Checks
The Gitlab Runner check currently provides a service check to ensure that the Runner can talk to the Gitlab master and another one to ensure that the
local Prometheus endpoint is available.

## Troubleshooting
Need help? Contact [Datadog Support](http://docs.datadoghq.com/help/).

## Further Reading
Learn more about infrastructure monitoring and all our integrations on [our blog](https://www.datadoghq.com/blog/)
