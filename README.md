# Faucet-freebitcoin

Bot de coleta automática de faucets das moedas freebitcoin.
Utiliza detector de captcha automático para h2captcha na versão 1, versão 2 ainda está em implementação.

### Requerimentos
Sistema operacional Windows.
Java 11 instalado.
Navegador Google Chrome

### Funcionalidades
- Configuração de mais de uma conta de usuário.
- Registro automático do usuário. "Scripts -> FreeBitcoin -> Efetuar registro".
> Necessidade de confirmação de email
- Modo silencioso( Não exibe o navegador)
Resolução de captchas usando inteligência artificial - [hcaptcha-model-factory](https://github.com/beiyuouo/hcaptcha-model-factory)
- Compartilhamento de promo codes com outros usuários do bot. (Canal no telegram)
- **27 modelos pré treinados**
- Atualização periódica de modelos, basta baixar e colocar na pasta!!!.

# Instruções para criação de novo treinamento de captcha

- Efetuar o download do projeto [hcaptcha-model-factory](https://github.com/beiyuouo/hcaptcha-model-factory)
	- Siga as instruções de instalação do projeto, com atenção aos requisitos de aplicativos python e pytorch.  [Instruções aqui](https://github.com/beiyuouo/hcaptcha-model-factory/wiki)
- Instalar ferramentas de compilação do visual studio (solicitadas durante a atualização das dependências do projeto).
- Efetuar a classificação das imagens.
	- Projeto Faucet-freebitcoin -> pasta imagens `<titulo_da_rede_a_ser_treinada>`
		- Classificar imagens válidas e inválidas

- Adicionar todas as imagens (válidas e inválidas) na pasta `unlabel`
- Criar mais 2 pastas `bad`e `yes`
	-	Adicionar imagens válidas na pasta `yes`
	-	Adicionar imagens inválidas na pasta `bad`
		```
		hcaptcha-model-factory
		 ├── data
		 │       ├──<titulo_da_rede_a_ser_treinada>
		 │       │		├── unlabel
		 │       │		├── bad 
		 │       │		├── yes 
		```

- na finalização do treinamento será gerado um arquivo no formato onnx, dentro da pasta ``hcaptcha-model-factory/model/<titulo_da_rede_a_ser_treinada>`` 

- Copiar o arquivo para a pasta  ``Faucet-freebitcoin/model``
