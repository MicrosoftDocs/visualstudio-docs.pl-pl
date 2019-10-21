---
title: Edytowanie arkuszy stylów XSLT
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 080bed0f-0ca9-4be7-aecd-6bdaebc04007
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7fc987f8362d5daf435b7e9de860cc13f16a1aaf
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72646057"
---
# <a name="edit-xslt-style-sheets"></a>Edytuj arkusze stylów XSLT

Edytor XML może również służyć do edytowania arkuszy stylów XSLT. Można korzystać z domyślnych funkcji edytora, takich jak IntelliSense, konspekty, fragmenty kodu XML i tak dalej. Ponadto dostępne są również nowe funkcje, które ułatwiają opracowywanie kodu XSLT.

## <a name="xslt-features"></a>Funkcje XSLT

W poniższej tabeli opisano funkcje specyficzne dla pracy z arkuszami stylów XSLT.

**Kolorowanie składni**

Słowa kluczowe XSLT, takie jak `template` i `match`, są wyświetlane w kolorze słowa kluczowego XSLT określonego w ustawieniach **czcionek i kolorów** .

**Faliste podkreślenie**

Edytor XML używa zainstalowanego pliku *XSLT. xsd* do walidacji arkuszy stylów XSLT. Błędy walidacji są wyświetlane jako niebieskie faliste podkreślenia. Edytor XML kompiluje także arkusz stylów w tle i raportuje błędy lub ostrzeżenia kompilatora z odpowiednimi falistymi podkreśleniami.

**Obsługa bloków skryptów**

Kod w blokach skryptu jest obsługiwany przez debuger XSLT, aby można było ustawić punkty przerwania i przejść przez kod bloku skryptu.

**Wyświetlanie danych wyjściowych XSLT**

Można wykonać transformację XSL i wyświetlić dane wyjściowe edytora XML. Aby uzyskać więcej informacji, zobacz [How to: Execute a XSLT Transformation from the XML editor](../xml-tools/how-to-execute-an-xslt-transformation-from-the-xml-editor.md).

**Debuguj kod XSLT**

Debuger XSLT można uruchomić z pliku XSLT w edytorze XML. Debuger obsługuje ustawianie punktów przerwania w pliku XSLT, wyświetlanie stanu wykonywania XSLT i tak dalej. Umieszczenie wskaźnika myszy na zmiennej XSLT powoduje wyświetlenie etykietki narzędzia z wartością zmiennej. Debuger może służyć do debugowania arkusza stylów lub debugowania skompilowanego przekształcenia XSL wywoływanego z innej aplikacji. Aby uzyskać więcej informacji, zobacz [debugowanie XSLT](../xml-tools/debugging-xslt.md).

## <a name="see-also"></a>Zobacz także

- [Edytor XML](../xml-tools/xml-editor.md)