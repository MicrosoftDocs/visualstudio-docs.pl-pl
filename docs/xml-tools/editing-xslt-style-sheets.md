---
title: Edytowanie arkuszy stylów XSLT
description: Dowiedz się więcej o funkcjach w edytorze XML do edytowania arkuszy stylów XSLT, w tym kolorowania składni, podkreśleń i uruchamiania debugera XSLT z edytora.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 080bed0f-0ca9-4be7-aecd-6bdaebc04007
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 31d961de62822bf036a898601ba0125db5a0dafc
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2020
ms.locfileid: "93045876"
---
# <a name="edit-xslt-style-sheets"></a>Edytuj arkusze stylów XSLT

Edytor XML może również służyć do edytowania arkuszy stylów XSLT. Można korzystać z domyślnych funkcji edytora, takich jak IntelliSense, konspekty, fragmenty kodu XML i tak dalej. Ponadto dostępne są również nowe funkcje, które ułatwiają opracowywanie kodu XSLT.

## <a name="xslt-features"></a>Funkcje XSLT

W poniższej tabeli opisano funkcje specyficzne dla pracy z arkuszami stylów XSLT.

**Kolorowanie składni**

Słowa kluczowe XSLT, takie jak `template` i `match` , są wyświetlane w kolorze słowa kluczowego XSLT określonego w ustawieniach **czcionek i kolorów** .

**Faliste podkreślenie**

Edytor XML używa zainstalowanego pliku *XSLT. xsd* do walidacji arkuszy stylów XSLT. Błędy walidacji są wyświetlane jako niebieskie faliste podkreślenia. Edytor XML kompiluje także arkusz stylów w tle i raportuje błędy lub ostrzeżenia kompilatora z odpowiednimi falistymi podkreśleniami.

**Obsługa bloków skryptów**

Kod w blokach skryptu jest obsługiwany przez debuger XSLT, aby można było ustawić punkty przerwania i przejść przez kod bloku skryptu.

**Wyświetlanie danych wyjściowych XSLT**

Można wykonać transformację XSL i wyświetlić dane wyjściowe edytora XML. Aby uzyskać więcej informacji, zobacz [How to: Execute a XSLT Transformation from the XML editor](../xml-tools/how-to-execute-an-xslt-transformation-from-the-xml-editor.md).

**Debugowanie XSLT**

Debuger XSLT można uruchomić z pliku XSLT w edytorze XML. Debuger obsługuje ustawianie punktów przerwania w pliku XSLT, wyświetlanie stanu wykonywania XSLT i tak dalej. Umieszczenie wskaźnika myszy na zmiennej XSLT powoduje wyświetlenie etykietki narzędzia z wartością zmiennej. Debuger może służyć do debugowania arkusza stylów lub debugowania skompilowanego przekształcenia XSL wywoływanego z innej aplikacji. Aby uzyskać więcej informacji, zobacz [debugowanie XSLT](../xml-tools/debugging-xslt.md).

## <a name="see-also"></a>Zobacz też

- [Edytor XML](../xml-tools/xml-editor.md)
