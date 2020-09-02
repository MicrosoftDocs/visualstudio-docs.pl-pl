---
title: Nie można przypisać do elementu "This" | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5000
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: ba2b0a2b-f0f8-4698-b335-a4ab6c166671
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f5c52153da64ff477d89b09d4af17169da18e4e1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85817323"
---
# <a name="cannot-assign-to-this"></a>Nie można przypisać do „tego"
Podjęto próbę przypisania wartości do **tego**elementu. jest **to** [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] słowo kluczowe, które odwołuje się do:

- Obiekt aktualnie wykonujący metodę,

- Obiekt globalny, jeśli nie ma bieżącej metody (lub metoda nie należy do żadnego innego obiektu).

Metoda jest [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] funkcją, która jest wywoływana za pomocą obiektu. Wewnątrz metody, słowo kluczowe **this** jest odwołaniem do obiektu, za pomocą którego wywołano metodę (co jest obiektem utworzonym przez wywoływanie konstruktora klasy z operatorem **New** ).

Wewnątrz metody, można jej użyć do odwoływania **się do bieżącego** obiektu, ale nie można przypisać do **niego**nowej wartości.

## <a name="to-correct-this-error"></a>Aby poprawić ten błąd

- Nie należy próbować przypisywać do **tego**elementu. Aby uzyskać dostęp do właściwości lub metody obiektu skonkretyzowanygo, użyj operatora kropki (np. **Circle. RADIUS**).

  > [!NOTE]
  > Nie można nazwać **zmiennej utworzonej**przez użytkownika; jest to [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] słowo zastrzeżone.

## <a name="see-also"></a>Zobacz też

- [this, instrukcja](../../javascript/reference/this-statement-javascript.md)
- [Rozwiązywanie problemów ze skryptami](../../javascript/advanced/troubleshooting-your-scripts-javascript.md)