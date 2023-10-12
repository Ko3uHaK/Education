### 1. Download Prometheus:
```bash
wget https://github.com/prometheus/prometheus/releases/download/<version>/prometheus-<version>linux-amd64.tar.gz
```
or download from official site:
https://prometheus.io/download/

### 2. Unpack the downloaded archive:
```bash
tar -xvzf prometheus-<version>.linux-amd64.tar.gz
```
### 3.  Create a directory and configuration file:
 - Create a directory for Prometheus:
```bash
mkdir -p /etc/prometheus
```
- Move the compiled Prometheus to the created directory:
```bash
mv prometheus-2.30.3.linux-amd64/prometheus /usr/local/bin/
mv prometheus-2.30.3.linux-amd64/promtool /usr/local/bin/
```
- Create a configuration file `prometheus.yml`:
```bash
nano /etc/prometheus/prometheus.yml
```
In this file you will define goals (targets) for monitoring and other settings. Here is a simple example of configuration:
```yaml
global:
  scrape_interval: 15s

scrape_configs:
  - job_name: 'prometheus'
    static_configs:
      - targets: ['localhost:9090']
```
### 4. Run Prometheus
```bash
prometheus --config.file=/etc/prometheus/prometheus.yml
```
### 5. Prometheus interface check:
Open your web browser and go to http://w_server:9090. You should see the Prometheus web interface.