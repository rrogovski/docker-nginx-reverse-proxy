# docker-nginx-reverse-proxy
Simple example docker using nginx reverse proxy

## About

Um projeto para a disciplina de redes, servidor web com proxy reverso usando nginx e docker. 

## How to use

```
git clone https://github.com/rrogovski/docker-nginx-reverse-proxy.git

cd docker-nginx-reverse-proxy

cd web01
```

Para criar o primeiro container com o webApp01, execute:

```
docker-compose build
```

E inicie o container com:

```
docker-compose up -d
```

Vamos fazer o mesmo para o webApp02:

```
cd ..

cd web02
```

Vamos criar o segundo container:

```
docker-compose build
```

E inicie o container com:

```
docker-compose up -d
```

Para ver os containers em execução:

```
docker container ls
```
Agora vamos ao container que será o nosso proxy:

```
cd ..

cd proxy
```

Aqui temos arquivos de configuração para que nginx faça o redirecionamento reverso para web01 e web02.

Importante também que faça a edição do seu arquivo /etc/hosts para o ip dos containers de web01 e web02. Para descobrir qual o ip desses containers faça:

```
docker container ls
```
![image](https://user-images.githubusercontent.com/10521603/127726617-3cfa75b3-6164-4d4a-872e-4308a5e49ee5.png)

Assim temos o ID dos container e podesmos usar os três primeiros identificadores da seguinte forma:

```
docker inspect f46 | grep IPAddress 
```

Assim temos o IP desse container:

![image](https://user-images.githubusercontent.com/10521603/127726705-f7067cd7-6f4f-442d-998b-e10829e57679.png)

Faça o mesmo para o outro container, e no arquivo /etc/hosts informe os IPs que obteve, no meu caso foi:

```
172.21.0.2 web01.test
172.22.0.2 web02.test
```

Considerando que ainda está dentro do diretório proxy, vamos criar o container, execute:

```
docker-compose build
```

E inicie o container com:

```
docker-compose up -d
```

E veja os containers em execução com:

```
docker container ls
```

Se tudo correu bem, você deve ter três containers:

![image](https://user-images.githubusercontent.com/10521603/127726897-973313ba-9848-49af-9441-e471f936d407.png)

Agora ao acessar localhost pelo browser temos:

![image](https://user-images.githubusercontent.com/10521603/127727020-5c6ef6c3-9cbb-468a-b7f7-ee7669fecbe3.png)
![image](https://user-images.githubusercontent.com/10521603/127727027-a2e39631-0851-46a9-b2d3-4b850241d356.png)
![image](https://user-images.githubusercontent.com/10521603/127727037-f71d962e-130e-4093-b13a-455323dd946c.png)
![image](https://user-images.githubusercontent.com/10521603/127727073-4b1377f7-2e2f-464d-a14d-1ab3c7f4e56f.png)
