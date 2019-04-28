---
title: Edytowanie arkuszy stylów XSLT
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 080bed0f-0ca9-4be7-aecd-6bdaebc04007
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dab4013bf3921a2af4f69d464c10d1e70f9407b3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62996993"
---
# <a name="edit-xslt-style-sheets"></a>Edytowanie arkuszy stylów XSLT

Edytor XML może również edytowanie arkuszy stylów XSLT. Można korzystać z zalet domyślny edytor funkcje, takie jak IntelliSense, tworzenie konspektu, w przypadku fragmentów kodu XML i tak dalej. Ponadto dostępne są także nowe funkcje, które ułatwiają tworzenie w kodzie XSLT.

## <a name="xslt-features"></a>Funkcje XSLT

W poniższej tabeli opisano funkcji przeznaczonych do pracy z arkuszy stylów XSLT.

**Kolorowanie składni**

Słowa kluczowe XSLT, takich jak `template` i `match`, są wyświetlane w kolorze — słowo kluczowe XSLT określonego przez **czcionki i kolory** ustawienia.

**Faliste podkreślenie**

Edytor XML używa zainstalowanych *xslt.xsd* plik, aby sprawdzić poprawność arkuszy stylów XSLT. Błędy sprawdzania poprawności są wyświetlane jako niebieskie faliste podkreślenia. Edytor XML kompiluje również arkusza stylów w tle i raporty o błędach kompilatora lub ostrzeżenia odpowiednie falistą.

**Obsługa blokach skryptu**

Kod w blokach skryptu jest obsługiwana przez debuger XSLT, dzięki czemu można ustawić punktów przerwania i Przechodź przez kod bloku skryptu.

**Wyświetlanie danych wyjściowych z XSLT**

Umożliwia wykonywanie transformacji XSL i wyświetlanie danych wyjściowych w edytorze XML. Aby uzyskać więcej informacji, zobacz [jak: Wykonywanie transformacji XSLT w edytorze XML](../xml-tools/how-to-execute-an-xslt-transformation-from-the-xml-editor.md).

**Debug XSLT**

Można uruchomić debuger XSLT z pliku XSLT w edytorze XML. Debuger obsługuje ustawianie punktów przerwania w pliku XSLT, wyświetlając stan wykonania XSLT i tak dalej. Kursor jest zmienna XSLT wywołuje etykietka narzędzia z wartością zmiennej. Debuger może służyć do debugowania arkuszy stylów lub Aby debugować skompilowanych przekształcenia XSL wywoływane z innej aplikacji. Aby uzyskać więcej informacji, zobacz [profilowanie XSLT](../xml-tools/debugging-xslt.md).

## <a name="see-also"></a>Zobacz także

- [Edytor XML](../xml-tools/xml-editor.md)