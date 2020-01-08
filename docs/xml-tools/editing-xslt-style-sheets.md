---
title: Edytowanie arkuszy stylów XSLT
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 080bed0f-0ca9-4be7-aecd-6bdaebc04007
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 81bab324c58c06cc1ca553bae2f81faf474c4ad0
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75592844"
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
