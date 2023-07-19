## Estornar Recebível

Estornar recebível na entidade, a qual o `fintera_api_token` pertence.

**Endpoint**

`PUT api/v1/receivables/<RECEIVABLE_ID>/refund`

```shell

curl --location --request PUT 'https://recebiveis.fintera.com.br/api/v1/receivables/705f17c5-5758-44e2-936b-6c3b34d6060e/refund' \
--header 'fintera_api_token: <SEU_FINTERA_API_TOKEN>' \
--header 'Content-Type: application/json' \
```

> O exemplo acima resulta o seguinte JSON:

```json
{
    "id": "705f17c5-5758-44e2-936b-6c3b34d6060e",
    "status": "refunded",
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
    "paid_value": "200.5",
    "expected_service_rate": null,
    "service_rate": null,
    "service_rate_check_status": "pending",
    "payment_check_status": "pending",
    "expected_payment_date": null,
    "paid_at": "2023-03-18",
    "customer_document": "1111111111111",
    "customer_name": "Joyce da Silva",
    "nfe_url": "https://www.exemplo.com/nfe/123456789",
    "entity_id": "bb9880e5-751c-45ed-a713-4a0a13768e7f",
    "created_at": "2023-03-16T15:34:55.983-03:00",
    "updated_at": "2023-03-16T15:34:55.983-03:00",
    "external_id": null,
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

**Status possíveis de estorno**

Atributo  | Valor | Descrição
--------- | ----------- | -----------
status | refunded | Estornado
status | refunde | A estornar

**Status inicial ao se solicitar um estorno**

Atributo  | Valor | Resposta
--------- | ----------- | -----------
payment_method | credit_card | refunded
payment_method | debit_card | refunded
payment_method | bank_transfer | refunde
payment_method | boleto | refunde
payment_method | cash | refunde
payment_method | pix | refunde
payment_method | bank_check | refunde
payment_method | others | refunde