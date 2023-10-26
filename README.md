# Estudo_Diagrama_Aplicativo_de_Viagem
Estudo pratico sobre diagramas referente ao curso da plataforma DIO, relembrar métodos, conteúdos e conceitos abordados.

```mermaid
flowchart TD;

    inicio_P((inicio))
    style inicio_P fill:green
    
subgraph Ações_Passageiro

    usuario_P(Usuário_Passageiro)
    cadastrarDados_P(Cadastrar nome e CPF)
    verDados_P(Verificar se já possui cadastro no CPF)
    decisao_P{Possui cadastro?}
    login_P(Mandar para área de login)
    cadastrarInfo_P(Cadastrar informação)
    informarPagamento(Informar forma de Pagamento)
    cartoes{Debito ou Crédito?}
    verC_Crédito(Verificar cartão de crédito)
    verC_Debito(Verificar cartão de debito)
    concluirCadastro_P(Concluir cadastro)
    enderecoPartida_P(Colocar Endereço de Partida)
    enderecoChegada_P(Colocar Endereço de Chegada)
    procurarMotorista(Esperar achar um motorista)
    style procurarMotorista fill:#663300,stroke:#BD7000,stroke-width:1px

        inicio_P-->usuario_P
        usuario_P-->cadastrarDados_P
        cadastrarDados_P-->verDados_P
        verDados_P-->decisao_P
        decisao_P--sim-->login_P
        decisao_P--nao-->cadastrarInfo_P
        cadastrarInfo_P-->informarPagamento
        informarPagamento-->cartoes
        cartoes--Crédito-->verC_Crédito  
        cartoes--Debito-->verC_Debito 
        verC_Crédito  & verC_Debito-->concluirCadastro_P
        concluirCadastro_P & login_P-->enderecoChegada_P
        enderecoChegada_P-->enderecoPartida_P
        enderecoPartida_P-->procurarMotorista
        aceitarCorrida--nao aceitou-->procurarMotorista
end


subgraph Ações_Motorista
    inicio_M((inicio))
    style inicio_M fill:green
    usuario_M(Usuário_Motorista)
    cadastrarDados_M(Cadastrar nome e CPF)
    verDados_M(Verificar se já possui cadastro no CPF)
    decisao_M{Possui cadastro?}
    login_M(Mandar para área de login)
    cadastrarInfo_M(Cadastrar informação)
    iniciarProcura(Iniciar procura de corridas)
    procurarCorridas(Procurar corridas por perto)
    style procurarCorridas fill:#663300,stroke:#BD7000,stroke-width:1px
    valorCorrida(Vizualizar o valor da corrida)
    pontoPassageiro(Mostrar o caminho para pegar o passageiro)
    destinoPassageiro(Mostrar caminho do destino do passageiro)
    receberPagamento(Receber pagamento)
    fim((Fim))
    style fim fill:red

        inicio_M-->usuario_M
        usuario_M-->cadastrarDados_M
        cadastrarDados_M-->verDados_M
        verDados_M-->decisao_M
        decisao_M--sim-->login_M
        decisao_M--nao-->cadastrarInfo_M
        cadastrarInfo_M & login_M-->iniciarProcura
        iniciarProcura-->procurarCorridas
        procurarCorridas-->valorCorrida
        aceitarCorrida--nao-->procurarCorridas
        aceitarCorrida--sim-->pontoPassageiro
        pontoPassageiro-->destinoPassageiro
        destinoPassageiro-->receberPagamento
        receberPagamento-->fim
        
end
        aceitarCorrida{Aceitar corrida?}
        valorCorrida-->aceitarCorrida
        procurarMotorista-->aceitarCorrida

```

<img src="./img/Diagrama de Serviço de transporte.jpg">
