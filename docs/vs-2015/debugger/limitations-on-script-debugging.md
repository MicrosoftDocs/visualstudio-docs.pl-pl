---
title: Ograniczenia debugowania skryptu | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- ASPX breakpoint mapping, limitations
- script debugging, limitations
- breakpoint mapping, limitations
ms.assetid: 280eead5-693c-47af-967f-dfe9d23f84db
caps.latest.revision: 25
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5ea088eadc09d45d576dd3c9cd33e5d9e2d79fc8
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68160629"
---
# <a name="limitations-on-script-debugging"></a>Ograniczenia debugowania skryptu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] obsługuje debugowanie skryptu po stronie klienta, z zastrzeżeniem ograniczeń w tym temacie.  
  
## <a name="limitations-on-breakpoint-mapping-with-client-side-script"></a>Ograniczenia dotyczące mapowanie punktów przerwania, za pomocą skryptu po stronie klienta  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] można ustawić punkt przerwania w pliku po stronie serwera ASPX lub kodu HTML, który jest przekształcany w pliku po stronie klienta w czasie wykonywania. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] mapuje punkt przerwania z pliku po stronie serwera do odpowiedniego punktu przerwania w pliku po stronie klienta, podlegają następującym ograniczeniom:  
  
- Można ustawić punktów przerwania, wewnątrz `<script>` bloków. Punkty przerwania w skrypcie wbudowanych lub `<% %>` bloki nie mogą być mapowane.  
  
- Adres URL przeglądarki dla strony musi zawierać nazwę strony. Na przykład http://microsoft.com/default.apsx. Mapowanie punktów przerwania nie może rozpoznać przekierowania z adresu takich jak http://microsoft.com do domyślnej strony.  
  
- Należy ustawić punkt przerwania w określonej w przeglądarce adres URL, a nie w pliku sterowania (ascx) ASPX strony głównej strony lub inny plik dołączony przez tę stronę. Nie można zamapować punkty przerwania ustawione na stronach uwzględnione.  
  
- Punkty przerwania ustawione w `<script defer=true>` bloki nie mogą być mapowane.  
  
- Aby ustawić punktów przerwania w `<script id="">` bloków, mapowanie punktów przerwania ignoruje `id` atrybutu.  
  
## <a name="breakpoint-mapping-and-duplicate-lines"></a>Mapowanie punktów przerwania lub zduplikowane wiersze  
 Aby znaleźć odpowiedniej lokalizacji w skrypt po stronie serwera i klienta, algorytm mapowanie punktu przerwania sprawdza, czy kod w każdym wierszu. Algorytm przyjęto założenie, że każdy wiersz jest unikatowa. Jeśli co najmniej dwa wiersze zawierają ten sam kod, a następnie ustaw punkt przerwania na jednym z tych zduplikowane wiersze, algorytm mapowanie punktu przerwania wybrać zduplikowany problem w pliku po stronie klienta. Aby tego uniknąć, należy dodać komentarz do wiersza, w którym ustawiono punkt przerwania. Przykład:  
  
```  
i++ ;  
i ++; // I added a comment, so this line is now unique  
i ++;  
```
