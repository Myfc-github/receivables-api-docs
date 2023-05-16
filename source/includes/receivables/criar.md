# Recebíveis

## Criar Recebível

Cria recebível na entidade, a qual o `fintera_api_token` pertence.

**Endpoint**

`POST api/v1/receivables`

```shell
curl --location --request POST 'https://recebiveis.fintera.com.br/api/v1/receivables' \
--header 'fintera_api_token: <SEU_FINTERA_API_TOKEN>' \
--header 'Content-Type: application/json' \
--data-raw '{
  "description": "Compra de roupas",
  "observation": "Pedido feito pelo site",
  "gross_value": 200.50,
  "payment_method": "credit_card",
  "acquirer_slug": "redecard",
  "card_brand": "mastercard",
  "payment_processed_at": "2023-03-16T13:59:59",
  "installment_number": 1,
  "installments_count": 1,
  "nsu": "1234567890",
  "authorization_code": "987654",
  "tid": "0123456789",
  "document": "202300001",
  "document_date": "2023-03-16",
  "customer_document": "1111111111111",
  "customer_name": "Joyce da Silva",
  "nfe_url": "https://www.exemplo.com/nfe/123456789"
}'
```

> O exemplo acima resulta o seguinte JSON:

```json
{
    "id": "705f17c5-5758-44e2-936b-6c3b34d6060e",
    "description": "Compra de roupas",
    "observation": "Pedido feito pelo site",
    "gross_value": "200.5",
    "payment_method": "credit_card",
    "acquirer_product": null,
    "payment_processed_at": "2023-03-16T13:59:59.000-03:00",
    "installment_number": 1,
    "installments_count": 1,
    "nsu": "1234567890",
    "authorization_code": "987654",
    "tid": "0123456789",
    "document": "202300001",
    "document_date": "2023-03-16",
    "expected_payment_value": null,
    "paid_value": null,
    "expected_service_rate": null,
    "service_rate": null,
    "service_rate_check_status": "pending",
    "payment_check_status": "pending",
    "expected_payment_date": null,
    "paid_at": null,
    "customer_document": "1111111111111",
    "customer_name": "Joyce da Silva",
    "nfe_url": "https://www.exemplo.com/nfe/123456789",
    "entity_id": "bb9880e5-751c-45ed-a713-4a0a13768e7f",
    "created_at": "2023-03-16T15:34:55.983-03:00",
    "updated_at": "2023-03-16T15:34:55.983-03:00",
    "external_id": null,
    "status": "liquidate",
    "integration_id": null,
    "bank_code": null,
    "bank_agency": null,
    "bank_account_number": null,
    "acquirer_slug": "redecard",
    "card_brand": "mastercard",
    "receivable_reconciliation_id": null,
    "payable_reconciliation_id": null,
    "cancellation_reason": null,
    "cancellation_adjustment_id": null,
    "anticipated": false
}
```

**Atributos do recebível**

Atributo  | Obrigatório | Descrição
--------- | ----------- | -----------
description | Não | Descrição do recebível.
observation | Não | Observações adicionais.
gross_value | Sim | O valor bruto do recebível, sem descontos ou taxas.
payment_method | Sim | A forma de pagamento (opções aceitas: _credit_card_, _debit_card_, _boleto_, _bank_transfer_, _pix_, _cash_).
acquirer_slug | Sim (caso payment_method é _credit_card_ ou _debit_card_)| O identificador da adquirente (opções aceitas: _redecard_)
card_brand | Sim (caso payment_method é _credit_card_ ou _debit_card_)| A bandeira do cartão de crédito utilizado (opções aceitas: _agiplan_, _amex_, _aura_, _banescard_, _banrisul_, _cabal_, _convenio_loja_, _credsystem_, _credz_, _diners_, _elo_, _hipercard_, _jcb_, _maestro_, _mastercard_, _outros_, _redecard_, _redeshop_, _sorocred_, _valecard_, _visa_, _visa_electron_)
payment_processed_at | Sim | A data e hora em que o pagamento foi processado.
installment_number | Sim (caso payment_method é _credit_card_) | O número da parcela.
installments_count | Sim (caso payment_method é _credit_card_) | O número total de parcelas.
nsu | Sim (caso payment_method é _credit_card_ ou _debit_card_) | Número sequencial único da transação, utilizado para identificar a transação junto à adquirente.
authorization_code | Sim (caso payment_method é _credit_card_ ou _debit_card_) | O código de autorização da transação.
tid | Não |  número de identificação da transação online.
document | Não | Número da Nota Fiscal.
document_date | Não |  Data da emissão da Nota Fiscal.
customer_document | Não | Documento (CPF/CNPJ) do cliente.
customer_name | Não | O nome do cliente
nfe_url | Não | A URL da Nota Fiscal.

## Criar Recebível Parcelado

Cria recebível parcelado na entidade, a qual o `fintera_api_token` pertence.

**Endpoint**

`POST api/v1/receivable_installments`

```shell
curl --location --request POST 'https://recebiveis.fintera.com.br/api/v1/receivable_installments' \
--header 'fintera_api_token: <SEU_FINTERA_API_TOKEN>' \
--header 'Content-Type: application/json' \
--data-raw '{
  "description": "Compra de roupas",
  "observation": "Pedido feito pelo site",
  "gross_value": 200.50,
  "payment_method": "credit_card",
  "acquirer_slug": "redecard",
  "card_brand": "mastercard",
  "payment_processed_at": "2023-03-16T13:59:59",
  "installments_count": 2,
  "nsu": "1234567890",
  "authorization_code": "987654",
  "tid": "0123456789",
  "document": "202300001",
  "document_date": "2023-03-16",
  "customer_document": "1111111111111",
  "customer_name": "Joyce da Silva",
  "nfe_url": "https://www.exemplo.com/nfe/123456789"
}'
```

> O exemplo acima resulta o seguinte JSON:

```json
[
  {
    "id": "a90f7656-ff66-4dab-b7b1-e0de767de09e",
    "description": "Compra de roupas",
    "observation": "Pedido feito pelo site",
    "gross_value": "100.25",
    "payment_method": "credit_card",
    "acquirer_product": null,
    "payment_processed_at": "2023-03-16T13:59:59.000-03:00",
    "installment_number": 1,
    "installments_count": 2,
    "nsu": "1234567890",
    "authorization_code": "987654",
    "tid": "0123456789",
    "document": "202300001",
    "document_date": "2023-03-16",
    "expected_payment_value": null,
    "paid_value": null,
    "expected_service_rate": null,
    "service_rate": null,
    "service_rate_check_status": "pending",
    "payment_check_status": "pending",
    "expected_payment_date": null,
    "paid_at": null,
    "customer_document": "1111111111111",
    "customer_name": "Joyce da Silva",
    "nfe_url": "https://www.exemplo.com/nfe/123456789",
    "entity_id": "bb9880e5-751c-45ed-a713-4a0a13768e7f",
    "created_at": "2023-05-16T08:24:06.625-03:00",
    "updated_at": "2023-05-16T08:24:06.625-03:00",
    "external_id": null,
    "status": "liquidate",
    "integration_id": null,
    "bank_code": null,
    "bank_agency": null,
    "bank_account_number": null,
    "acquirer_slug": "redecard",
    "card_brand": "mastercard",
    "receivable_reconciliation_id": null,
    "payable_reconciliation_id": null,
    "anticipated": false,
    "cancellation_reason": null,
    "cancellation_adjustment_id": null
  },
  {
    "id": "d4ce9c43-769f-4a97-a857-ed755bb6ccd7",
    "description": "Compra de roupas",
    "observation": "Pedido feito pelo site",
    "gross_value": "100.25",
    "payment_method": "credit_card",
    "acquirer_product": null,
    "payment_processed_at": "2023-03-16T13:59:59.000-03:00",
    "installment_number": 2,
    "installments_count": 2,
    "nsu": "1234567890",
    "authorization_code": "987654",
    "tid": "0123456789",
    "document": "202300001",
    "document_date": "2023-03-16",
    "expected_payment_value": null,
    "paid_value": null,
    "expected_service_rate": null,
    "service_rate": null,
    "service_rate_check_status": "pending",
    "payment_check_status": "pending",
    "expected_payment_date": null,
    "paid_at": null,
    "customer_document": "1111111111111",
    "customer_name": "Joyce da Silva",
    "nfe_url": "https://www.exemplo.com/nfe/123456789",
    "entity_id": "bb9880e5-751c-45ed-a713-4a0a13768e7f",
    "created_at": "2023-05-16T08:24:06.632-03:00",
    "updated_at": "2023-05-16T08:24:06.632-03:00",
    "external_id": null,
    "status": "liquidate",
    "integration_id": null,
    "bank_code": null,
    "bank_agency": null,
    "bank_account_number": null,
    "acquirer_slug": "redecard",
    "card_brand": "mastercard",
    "receivable_reconciliation_id": null,
    "payable_reconciliation_id": null,
    "anticipated": false,
    "cancellation_reason": null,
    "cancellation_adjustment_id": null
  }
]
```

**Atributos do recebível parcelado**

Atributo  | Obrigatório | Descrição
--------- | ----------- | -----------
description | Não | Descrição do recebível.
observation | Não | Observações adicionais.
gross_value | Sim | O valor bruto do recebível, sem descontos ou taxas.
payment_method | Sim | A forma de pagamento (opções aceitas: _credit_card_, _debit_card_, _boleto_, _bank_transfer_, _pix_, _cash_).
acquirer_slug | Sim (caso payment_method é _credit_card_ ou _debit_card_) | O identificador da adquirente (opções aceitas: _redecard_)
card_brand | Sim (caso payment_method é _credit_card_ ou _debit_card_)| A bandeira do cartão de crédito utilizado (opções aceitas: _agiplan_, _amex_, _aura_, _banescard_, _banrisul_, _cabal_, _convenio_loja_, _credsystem_, _credz_, _diners_, _elo_, _hipercard_, _jcb_, _maestro_, _mastercard_, _outros_, _redecard_, _redeshop_, _sorocred_, _valecard_, _visa_, _visa_electron_)
payment_processed_at | Sim | A data e hora em que o pagamento foi processado.
installment_number | Não | O número da parcela.
installments_count | Sim | O número total de parcelas.
nsu | Sim (caso payment_method é _credit_card_ ou _debit_card_) | Número sequencial único da transação, utilizado para identificar a transação junto à adquirente.
authorization_code | Sim (caso payment_method é _credit_card_ ou _debit_card_) | O código de autorização da transação.
tid | Não |  número de identificação da transação online.
document | Não | Número da Nota Fiscal.
document_date | Não |  Data da emissão da Nota Fiscal.
customer_document | Não | Documento (CPF/CNPJ) do cliente.
customer_name | Não | O nome do cliente
nfe_url | Não | A URL da Nota Fiscal.
