---
created: 20221130-1738
tags:
  - refactor
---


# Refactor: Extract method

> Turn a fragment of code into a method whose name explains it's purpose.

Si hay que comentar un pedazo de código tal vez es mejor separarlo en su propio método para que sea explicativo.

El método updateAssociatedDeal se entiende mejor en medio del código que el condicional de debajo. Es más 'Verboso', pero se gana en cláridad a la hora de volver sobre el código semanas o meses después.

    $this->updateAssociatedDeal($request, $cashR);

El comentario estaba antes en el código junto con el if, antes de ser separado en su propio método. Ahora es redundante pero sirve para explicar el punto.

    /*** update operation amount paid */
    private function updateAssociatedDeal($request, $cashR){
      if ($request->has('deal_id')) {
        $this->updateOperationAmount($request, $cashR);
      } else {
        if ($request->has('invoices')) { $this->saveInvoices($request['invoices'], $cashR); }
      }
    }

---
# References
