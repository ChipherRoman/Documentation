# API Documentation

## Overview

This API provides an endpoint for analyzing and validating Anotações de
Responsabilidade Técnica (ART) for engineering and construction projects. The
analysis is performed using the Anthropic API and results are stored in a
Firestore database.

## Overview (Portuguese)

Esta API fornece um endpoint para análise e validação de Anotações de
Responsabilidade Técnica (ART) para projetos de engenharia e construção. A
análise é realizada usando a API Anthropic e os resultados são armazenados em um
banco de dados Firestore.

## Endpoint

### `/analyse`

#### Method

`POST`

#### URL
Test Address: http://142.93.50.250:5000/analyse

`/analyse`

#### Request Format

The request should be a JSON object containing the ART data to be analyzed.
Below is an example of the expected input:

```json
{
    "tipoArt": "OBRA / SERVIÇO",
    "finalidade": "SEM DEFINIÇÃO",
    "participacao_tecnica": "INDIVIDUAL",
    "entidade": "SEM INDICACAO DE ENTIDADE DE CLASSE",
    "forma_registro": "INICIAL",
    "observacao": "Elaboração de projeto de fundação e estruturas metálicas.",
    "qtdAtividades": 2,
    "atividades": [
        {
            "nivel": "Elaboração",
            "atividade_subordinada": "ESTRUTURAS > FUNDAÇÕES > DE FUNDAÇÕES PROFUNDAS > #2.9.2.3 - EM ESTACAS DE CONCRETO MOLDADAS IN LOCO",
            "atividade_servico": "80 - Projeto",
            "quantidade": "3,00",
            "unidade_medida": "metro cúbico "
        }
    ]
}
```
