---
title: Ograniczenia dotyczące debugowania skryptów | Microsoft Docs
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
ms.openlocfilehash: 9f4f8f1e2fb014dc812bb5980d333e0a851f9222
ms.sourcegitcommit: 374f5ec9a5fa18a6d4533fa2b797aa211f186755
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/20/2020
ms.locfileid: "77476814"
---
# <a name="limitations-on-script-debugging"></a>Ograniczenia debugowania skryptu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] obsługuje debugowanie skryptu po stronie klienta, zgodnie z ograniczeniami w tym temacie.  
  
## <a name="limitations-on-breakpoint-mapping-with-client-side-script"></a>Ograniczenia dotyczące mapowania punktów przerwania za pomocą skryptu po stronie klienta  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] umożliwia ustawienie punktu przerwania w pliku ASPX lub HTML po stronie serwera, który jest przekształcany na plik po stronie klienta w czasie wykonywania. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] mapuje punkt przerwania z pliku po stronie serwera do odpowiedniego punktu przerwania w pliku po stronie klienta, z uwzględnieniem następujących ograniczeń:  
  
- Punkty przerwania muszą być ustawione wewnątrz bloków `<script>`. Nie można zamapować punktów przerwania w skrypcie wbudowanym lub blokach `<% %>`.  
  
- Adres URL przeglądarki dla strony musi zawierać nazwę strony. Na przykład `http://microsoft.com/default.apsx`. Mapowanie punktów przerwania nie może rozpoznać przekierowania z adresu, takiego jak `http://microsoft.com`, do domyślnej strony.  
  
- Punkt przerwania musi być ustawiony na stronie określonej w adresie URL przeglądarki, a nie w pliku kontrolki ASPX (ascx), stronie wzorcowej ani w innym pliku dołączonym do tej strony. Nie można zamapować punktów przerwania ustawionych na uwzględnionych stronach.  
  
- Nie można zamapować punktów przerwania ustawionych w blokach `<script defer=true>`.  
  
- W przypadku punktów przerwania ustawionych w blokach `<script id="">` mapowanie punktów przerwania ignoruje atrybut `id`.  
  
## <a name="breakpoint-mapping-and-duplicate-lines"></a>Mapowanie punktów przerwania i zduplikowane linie  
 Aby znaleźć odpowiednią lokalizację w skrypcie po stronie serwera i po stronie klienta, algorytm mapowania punktu przerwania bada kod w każdym wierszu. Algorytm zakłada, że każdy wiersz jest unikatowy. Jeśli co najmniej dwie linie zawierają ten sam kod i ustawisz punkt przerwania dla jednego z tych zduplikowanych wierszy, algorytm mapowania punktu przerwania może wybrać nieprawidłowy duplikat w pliku po stronie klienta. Aby tego uniknąć, Dodaj komentarz do wiersza, w którym ustawiono punkt przerwania. Na przykład:  
  
```  
i++ ;  
i ++; // I added a comment, so this line is now unique  
i ++;  
```
