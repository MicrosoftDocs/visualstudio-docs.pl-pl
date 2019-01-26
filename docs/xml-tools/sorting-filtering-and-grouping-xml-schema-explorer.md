---
title: Sortowanie, filtrowanie i grupowanie w Eksplorator schematu XML
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: 4a914de0-9ffc-4526-9603-92e460e52513
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c14f19ab19659d85c20021f64796c2bcfb5f2a81
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54926270"
---
# <a name="sorting-filtering-and-grouping-xml-schema-explorer"></a>Sortowanie, filtrowanie i grupowanie (Eksplorator schematu XML)

W tym temacie opisano opcje, które są dostępne za pośrednictwem **opcje grupowanie, filtrowanie i sortowanie** menu **Eksploratora schematu XML** paska narzędzi.

## <a name="filter-options"></a>Opcje filtru

 Dostępne są następujące opcje filtru. Domyślnie **Pokaż przestrzenie nazw** i **Pokaż pliki schematu** są zaznaczone opcje.

-   **Pokaż przestrzenie nazw**.

-   **Pokaż pliki schematu**.

-   **Pokaż Kompozytory (sekwencji/wyboru/all)**.

## <a name="sorting-options"></a>Opcje sortowania

 Dostępne są następujące opcje sortowania. Wartość domyślna to **sortowania według typu**. **Sortuj według** opcje nie są stosowane do plików i przestrzeni nazw.

-   **Sortuj według typu**.

-   **Sortuj według nazwy**.

-   **Dokumentowanie kolejności**.

### <a name="sort-by-type"></a>Sortuj według typu

 Gdy **sortowania według typu** opcja jest zaznaczona, globalne węzły są sortowane w następującej kolejności. Węzły są posortowane alfabetycznie w każdej grupie.

1.  `import` węzły.

2.  `include` węzły.

3.  `redefine` węzły.

4.  `attribute` węzły.

5.  `attributeGroup` węzły.

6.  `complexType` węzły.

7.  `simpleType` węzły.

8.  `element` węzły.

9. `group` węzły.

### <a name="sort-by-name"></a>Sortuj według nazwy

 Gdy **Sortuj według nazwy** opcja jest zaznaczona, globalne węzły są sortowane w następującej kolejności:

1.  `import` węzły (w kolejności alfabetycznej według przestrzeni nazw).

2.  `include` węzły (w kolejności alfabetycznej według `schemaLocation` atrybutów).

3.  `redefine` węzły (w kolejności alfabetycznej według `schemaLocation` atrybutów).

4.  Inne węzły globalne w kolejności alfabetycznej.

### <a name="document-order"></a>Kolejności dokumentu

 **Kolejności dokumentu** opcja jest dostępna, gdy **Pokaż pliki schematu** opcja jest zaznaczona. Gdy **kolejności dokumentu** jest zaznaczone, globalne węzły są wyświetlane w kolejności, w jakiej występują w pliku schematu.

## <a name="persisting-sortfilter-options"></a>Utrwalanie opcje sortowania/filtrowania

 Sortowanie, filtrowanie i grupowanie opcje są zapisywane w rejestrze dla każdego użytkownika, niezależnie od tego, które rozwiązanie lub pliki były otwarte podczas ustawienia zostały zmienione.