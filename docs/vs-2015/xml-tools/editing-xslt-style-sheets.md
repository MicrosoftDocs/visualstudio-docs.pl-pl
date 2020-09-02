---
title: Edytowanie arkuszy stylów XSLT | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 080bed0f-0ca9-4be7-aecd-6bdaebc04007
caps.latest.revision: 11
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3e1669affa89c91ca3ae1958c22ff3ec4d56bb8c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670952"
---
# <a name="editing-xslt-style-sheets"></a>Edytowanie arkuszy stylów XSLT
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Edytor XML może również służyć do edytowania arkuszy stylów XSLT. Można korzystać z domyślnych funkcji edytora, takich jak IntelliSense, konspekty, fragmenty kodu XML i tak dalej. Ponadto dostępne są również nowe funkcje, które ułatwiają opracowywanie kodu XSLT.

## <a name="xslt-features"></a>Funkcje XSLT
 W poniższej tabeli opisano funkcje specyficzne dla pracy z arkuszami stylów XSLT.

 **Kolorowanie składni** Słowa kluczowe XSLT, takie jak `template` , `match` i tak dalej, są wyświetlane w kolorze słowa kluczowego XSLT określonego przez **Ustawienia Fonts i Colors** .

 **Faliste podkreślenie** Edytor XML używa zainstalowanego pliku XSLT. xsd do walidacji arkuszy stylów XSLT. Błędy walidacji są wyświetlane jako niebieskie faliste podkreślenia. Edytor XML kompiluje także arkusz stylów w tle i raportuje błędy lub ostrzeżenia kompilatora z odpowiednimi falistymi podkreśleniami.

 **Obsługa bloków skryptów** Kod w blokach skryptu jest obsługiwany przez debuger XSLT, aby można było ustawić punkty przerwania i przejść przez kod bloku skryptu.

 **Wyświetlanie danych wyjściowych XSLT** Można wykonać transformację XSL i wyświetlić dane wyjściowe edytora XML. Aby uzyskać więcej informacji, zobacz [How to: Execute a XSLT Transformation from the XML editor](../xml-tools/how-to-execute-an-xslt-transformation-from-the-xml-editor.md).

 **Debuguj kod XSLT** Debuger XSLT można uruchomić z pliku XSLT w edytorze XML. Debuger obsługuje ustawianie punktów przerwania w pliku XSLT, wyświetlanie stanu wykonywania XSLT i tak dalej. Umieszczenie wskaźnika myszy na zmiennej XSLT powoduje wyświetlenie etykietki narzędzia z wartością zmiennej. Debuger może służyć do debugowania arkusza stylów lub debugowania skompilowanego przekształcenia XSL wywoływanego z innej aplikacji. Aby uzyskać więcej informacji, zobacz [debugowanie XSLT](../xml-tools/debugging-xslt.md).

## <a name="see-also"></a>Zobacz też
 [Edytor XML](../xml-tools/xml-editor.md)
