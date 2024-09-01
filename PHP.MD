# How to Implement in PHP 5.6

This section provides a step-by-step guide on how to implement the API in PHP
5.6.

## Prerequisites

- PHP 5.6
- Composer
- cURL extension enabled

## Step 1: Set Up Your Project

1. Create a new directory for your project and navigate into it:

   ```bash
   mkdir art-analysis-api
   cd art-analysis-api
   ```

2. Initialize a new Composer project:

   ```bash
   composer init --name="yourname/art-analysis-api" --require="guzzlehttp/guzzle:^6.0" --no-interaction
   ```

3. Install the Guzzle HTTP client:

   ```bash
   composer install
   ```

## Step 2: Create the Request

Create a new PHP file named `analyse.php` and add the following code:

```php
<?php

require 'vendor/autoload.php';

use GuzzleHttp\Client;

$client = new Client([
    'base_uri' => 'http://your-api-url',
    'headers' => [
        'Content-Type' => 'application/json',
        'Authorization' => 'Bearer YOUR_API_KEY'
    ]
]);

$data = [
    "numero" => "MA20240798474",
    "tipoArt" => "OBRA / SERVIÇO",
    "finalidade" => "SEM DEFINIÇÃO",
    "participacao_tecnica" => "INDIVIDUAL",
    "entidade" => "SEM INDICACAO DE ENTIDADE DE CLASSE",
    "forma_registro" => "INICIAL",
    "observacao" => "Elaboração de projeto de fundação e estruturas metálicas.",
    "qtdAtividades" => 2,
    "qtdArtsVinculadasParticipacaoTecnica" => 0,
    "qtdArtsVinculadasFormaRegistro" => 0,
    "atividades" => [
        [
            "nivel" => "Elaboração",
            "atividade_subordinada" => "ESTRUTURAS > FUNDAÇÕES > DE FUNDAÇÕES PROFUNDAS > #2.9.2.3 - EM ESTACAS DE CONCRETO MOLDADAS IN LOCO",
            "atividade_servico" => "80 - Projeto",
            "quantidade" => "3,00",
            "unidade_medida" => "metro cúbico "
        ],
        [
            "nivel" => "Elaboração",
            "atividade_subordinada" => "ESTRUTURAS > ESTRUTURAS METÁLICAS > DE ESTRUTURA METÁLICA > #2.2.1.7 - PARA FINS DIVERSOS",
            "atividade_servico" => "80 - Projeto",
            "quantidade" => "3,00",
            "unidade_medida" => "metro cúbico "
        ]
    ]
];

$response = $client->post('/analyse', [
    'json' => $data
]);

$body = $response->getBody();
$responseData = json_decode($body, true);

echo "Is Approved: " . ($responseData['is_approved'] ? 'Yes' : 'No') . "\n";
echo "Description: " . $responseData['description'] . "\n";
```
