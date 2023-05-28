create instance and connect with ssh


![image](https://github.com/imtiaz04/Grfana_loki_promtail/assets/85178565/335fcae3-8b53-4417-9a77-d48e3386323b)
 
update system

![image](https://github.com/imtiaz04/Grfana_loki_promtail/assets/85178565/229e27ba-a9b2-42dd-a748-c5a048d6cc39)


Install Grafana on Debian or Ubuntu

![image](https://github.com/imtiaz04/Grfana_loki_promtail/assets/85178565/c7807b64-cd94-47ac-81a7-04375c3d827e)

adding Stable release and install grafana on ec2

echo "deb [signed-by=/usr/share/keyrings/grafana.key] https://apt.grafana.com stable main" | sudo tee -a /etc/apt/sources.list.d/grafana.list

![image](https://github.com/imtiaz04/Grfana_loki_promtail/assets/85178565/65edca2f-d7e2-40fb-8423-998e733e9cee)

start , enable grafana


![image](https://github.com/imtiaz04/Grfana_loki_promtail/assets/85178565/9db7c274-b262-4e18-a158-d4380666e63d)

![image](https://github.com/imtiaz04/Grfana_loki_promtail/assets/85178565/e3c0fd21-4add-4e66-8ce4-91dbbe0e9dab)


install docker

![image](https://github.com/imtiaz04/Grfana_loki_promtail/assets/85178565/011c6050-bbf5-4b69-b213-f26ee7b68b94)

docker ps you will see container & give permissions & restart & ssh with ec2 instance

![image](https://github.com/imtiaz04/Grfana_loki_promtail/assets/85178565/c9acd7f7-69d6-466d-95be-61402288c674)

Download Loki Config


wget https://raw.githubusercontent.com/grafana/loki/v2.8.0/cmd/loki/loki-local-config.yaml -O loki-config.yaml



![image](https://github.com/imtiaz04/Grfana_loki_promtail/assets/85178565/2dd7ccaa-6ac3-422a-9417-b0421c99db4e)


![image](https://github.com/imtiaz04/Grfana_loki_promtail/assets/85178565/ac3b4f62-29df-40e3-bd45-cb254a5b0b2f)


Download Promtail Config

wget https://raw.githubusercontent.com/grafana/loki/v2.8.0/clients/cmd/promtail/promtail-docker-config.yaml -O promtail-config.yaml


![image](https://github.com/imtiaz04/Grfana_loki_promtail/assets/85178565/eac5d01e-a9b4-4c60-925e-df52aa9f082a)


![image](https://github.com/imtiaz04/Grfana_loki_promtail/assets/85178565/12c949f9-8c09-40d0-989d-5b60743f2fba)

Run Loki Docker container

docker run -d --name loki -v $(pwd):/mnt/config -p 3100:3100 grafana/loki:2.8.0 --config.file=/mnt/config/loki-config.yaml

![image](https://github.com/imtiaz04/Grfana_loki_promtail/assets/85178565/ab75c8f1-aa7d-4410-a684-bab9b42b917c)

![image](https://github.com/imtiaz04/Grfana_loki_promtail/assets/85178565/7836c25b-bfe5-4987-b192-6a0a155cebd5)

Run Promtail Docker container

docker run -d --name promtail -v $(pwd):/mnt/config -v /var/log:/var/log --link loki grafana/promtail:2.8.0 --config.file=/mnt/config/promtail-config.yaml

![image](https://github.com/imtiaz04/Grfana_loki_promtail/assets/85178565/087dbb25-1de1-48fb-b40a-06b3a6a6303b)

![image](https://github.com/imtiaz04/Grfana_loki_promtail/assets/85178565/d8a8e7dd-475d-4d89-b72b-d597c3026e34)


add pwd path in prom-tail config file

![image](https://github.com/imtiaz04/Grfana_loki_promtail/assets/85178565/6c478858-666c-4241-83b2-4a50d1cca57b)

![image](https://github.com/imtiaz04/Grfana_loki_promtail/assets/85178565/619a7d61-c00b-4f1a-aa01-83a9e181bf06)

install nginx

add data-source to grafana

![image](https://github.com/imtiaz04/Grfana_loki_promtail/assets/85178565/c2b74e47-d061-411b-9f0a-19411d7957c9)


![image](https://github.com/imtiaz04/Grfana_loki_promtail/assets/85178565/5f1ef394-6f16-4d10-a09b-5ba3db42aada)

![image](https://github.com/imtiaz04/Grfana_loki_promtail/assets/85178565/bc12b535-283d-45be-9b0b-01e34e3f0cf5)

give url of the promtail 

![image](https://github.com/imtiaz04/Grfana_loki_promtail/assets/85178565/a2c9e663-a3dc-4069-859b-b56d0a6d54d7)

save & run test

![image](https://github.com/imtiaz04/Grfana_loki_promtail/assets/85178565/0fe9ba90-69a1-45b4-9211-17a0deda59af)

go to explore select lables>job>select vlaue>var logs >run quary


![image](https://github.com/imtiaz04/Grfana_loki_promtail/assets/85178565/12020e54-4b5a-4c52-b206-a6470792bdbb)

![image](https://github.com/imtiaz04/Grfana_loki_promtail/assets/85178565/0ca9709f-cf98-4f41-983a-7126bedb6444)

![image](https://github.com/imtiaz04/Grfana_loki_promtail/assets/85178565/59bd863c-3f88-4f19-b8f7-63a4f47c6ea7)


![image](https://github.com/imtiaz04/Grfana_loki_promtail/assets/85178565/dae05699-b21d-43a1-9b16-23b62b20b0fa)







