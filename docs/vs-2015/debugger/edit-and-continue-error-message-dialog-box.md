---
title: Edytuj i Kontynuuj — okno dialogowe komunikat o błędzie | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.ENC.SupportedButNotAvailable
- vs.debug.ENC.CannotEditWhileException
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Edit and Continue Error Message dialog box
ms.assetid: f98c91c0-447a-4533-85b6-87170a0dc4c3
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 73018dcdc34d3a824ff13da13fc12d03b8d13a7e
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54788601"
---
# <a name="edit-and-continue-error-message-dialog-box"></a>Komunikat o błędzie Edytuj i kontynuuj — Okno dialogowe
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

To okno dialogowe pojawia się podczas debugowania w języku, który obsługuje Edit and Continue, ale **Edytuj i Kontynuuj** nie jest dostępna tylko dla typu zmiany kodu, które zostały wprowadzone. Komunikat o błędzie wewnątrz pola zapewnia bardziej szczegółowy opis. Możliwe przyczyny wyświetlania tego okna dialogowego obejmują:  
  
-   Próbowano edytować kodu zarządzanego, gdy debugowanie niezarządzane została włączona. Edytuj i Kontynuuj nie działa w debugowaniu trybu mieszanego.  
  
-   Podjęto próbę edytowania kodu programu SQL Server.  
  
-   Podjęto próbę edytowania kodu podczas debugowania odzyskiwania po awarii. Zrzut programu Watson.  
  
-   Próbowano edytować kod po Wystąpił nieobsługiwany wyjątek i opcji "**Unwind na stosie wywołań dotycząca nieobsłużonych wyjątków**" nie został wybrany.  
  
-   Podjęto próbę edytowania kodu podczas debugowania aplikacji osadzonego środowiska uruchomieniowego.  
  
-   Próbowano edytować kodu w programie, który został załączony do zamiast od **debugowania** menu.  
  
-   Próbowano edytować zoptymalizowanego kodu.  
  
-   Próbowano edytować kodu zarządzanego, gdy obiektem docelowym jest aplikacją 64-bitową. Jeśli chcesz Użyj funkcji Edytuj i Kontynuuj, należy ustawić element docelowy x86. (*Projektu* **właściwości**, **skompilować** karcie **zaawansowane kompilatora** ustawienie.).  
  
-   Próbowano edytować kod w zestawie, który został zmodyfikowany podczas debugowania i został załadowany ponownie.  
  
-   Próbowano edytować kod w zestawie, który nie został załadowany.  
  
-   Rozpoczęto profilowanie starą wersję aplikacji (ponieważ jest to nowa wersja ma błędy kompilacji).  
  
-   Podjęto próbę edytowania kodu została uruchomiona.  
  
## <a name="uielement-list"></a>Lista elementów UI  
 **OK**  
 Zamknij okno dialogowe i Anuluj bezpośrednio poprzednie próby edycji.  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługiwane zmiany kodu (C++)](../debugger/supported-code-changes-cpp.md)
