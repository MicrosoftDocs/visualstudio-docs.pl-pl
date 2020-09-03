---
title: Uzupełnianie instrukcji dla identyfikatorów | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- IntelliSense [JavaScript], statement completion
- statement completion, JavaScript IntelliSense
ms.assetid: c2cd4945-c67e-471b-8057-96cfd25f7fb2
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f5e52bf174e5a41d79fa23bfca39121db668e40e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72643857"
---
# <a name="statement-completion-for-identifiers"></a>Uzupełnianie składni dla identyfikatorów
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Język JavaScript nie dopuszcza jawnego wpisywania dla deklaracji zmiennych. W związku z tym technologia IntelliSense nie zawsze zapewnia listy uzupełniania dla obiektów. Może się to zdarzyć w różnych sytuacjach. Poniżej przedstawiono kilka typowych.

- Parametr jest zadeklarowany, ale nie został wywołany w innym miejscu w aktywnym dokumencie, jak pokazano w poniższym przykładzie.

  ```javascript
  function illuminate(light) {
           light.  // Accurate statement completion is not available
                   // unless illuminate is called elsewhere with a
                   // parameter that has a value. If it is called only
                   // in a function that is a sibling to
                   // illuminate(light) in the call hierarchy, the
                   // IntelliSense engine also cannot determine the
                   // parameter type.
       }

  // Sibling function. No statement completion for light
  // object in preceding code.
  function lightLamp() {
      var x = illuminate(1);
  }

  // Uncomment the next line to obtain statement completion for
  // light object in preceding code.
  // var x = illuminate(1);
  ```

- Obiekt znajduje się w funkcji, która jest wywoływana w odpowiedzi na zdarzenie. W czasie projektowania aparat IntelliSense nie może określić typu obiektów używanych w tej sytuacji.

   Jeśli aparat IntelliSense może określić, że zdarzenie ma zostać wywołane, zwykle przez użycie `addEventListener` dla zdarzenia w aktywnym dokumencie, dostępne są bardziej dokładne informacje IntelliSense.

  Gdy technologia IntelliSense nie może zidentyfikować obiektu, aparat IntelliSense wypełnia listę uzupełniania nazwanymi jednostkami lub identyfikatorami, które znajdują się w aktywnym dokumencie. Gdy lista uzupełniania zawiera te identyfikatory, obok nich są wyświetlane ikony informacji. Ponadto etykietka narzędzia dla każdego identyfikatora wskazuje, że wyrażenie jest nieznane. Na poniższej ilustracji przedstawiono opcje uzupełniania instrukcji dla obiektu typu `light` , którego nie można zidentyfikować, ponieważ obiekt i jego właściwości są niezdefiniowane. Jednak `intensity` Właściwość jest dostępna na liście identyfikatorów, ponieważ została użyta w `illuminate` funkcji.

  **Opcje uzupełniania dla obiektu, którego nie można zidentyfikować**

  ![Funkcja IntelliSense języka JavaScript dla identyfikatorów](../ide/media/js-intellisense-identifiers.png "js_intellisense_identifiers")

  Listę uzupełniania dla obiektu można przesłonić, korzystając z komentarzy do dokumentacji XML lub funkcji rozszerzenia JavaScript IntelliSense. Korzystając z tych funkcji, możesz podać informacje o typie i więcej opisowych informacji IntelliSense, gdy może nie być dostępny w inny sposób. Aby uzyskać więcej informacji, zobacz [Rozszerzanie kodu JavaScript IntelliSense](../ide/extending-javascript-intellisense.md) i [tworzenie komentarzy do dokumentacji XML](../ide/create-xml-documentation-comments-for-javascript-intellisense.md).

## <a name="see-also"></a>Zobacz też
 [JavaScript IntelliSense](../ide/javascript-intellisense.md)
