---
title: Sortowanie, filtrowanie i grupowanie w Eksploratorze schematu XML
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 4a914de0-9ffc-4526-9603-92e460e52513
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6bf9226f3b491a39c7ef5936667cabd789c6a457
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72604580"
---
# <a name="sorting-filtering-and-grouping-xml-schema-explorer"></a>Sortowanie, filtrowanie i grupowanie (Eksplorator schematu XML)

W tym temacie opisano opcje, które są dostępne w menu **Opcje sortowania, filtrowania i grupowania** na pasku narzędzi **Eksploratora schematu XML** .

## <a name="filter-options"></a>Opcje filtru

Dostępne są następujące opcje filtra. Domyślnie są zaznaczone opcje **Pokaż obszary nazw** i **Pokaż pliki schematu** .

- **Pokaż przestrzenie nazw**.

- **Pokaż pliki schematu**.

- **Pokaż kompozytory (sekwencja/wybór/wszystko)** .

## <a name="sorting-options"></a>Opcje sortowania

Dostępne są następujące opcje sortowania. Wartość domyślna to **Sortuj według typu**. **Sortowanie według** opcji nie dotyczy plików i przestrzeni nazw.

- **Sortuj według typu**.

- **Sortuj według nazwy**.

- **Kolejność dokumentów**.

### <a name="sort-by-type"></a>Sortuj według typu

W przypadku wybrania opcji **Sortuj według typu** węzły globalne są sortowane w następującej kolejności. Węzły są następnie sortowane alfabetycznie w każdej grupie.

1. `import` węzły.

2. `include` węzły.

3. `redefine` węzły.

4. `attribute` węzły.

5. `attributeGroup` węzły.

6. `complexType` węzły.

7. `simpleType` węzły.

8. `element` węzły.

9. `group` węzły.

### <a name="sort-by-name"></a>Sortuj według nazwy

W przypadku wybrania opcji **Sortuj według nazwy** węzły globalne są sortowane w następującej kolejności:

1. węzły `import` (w kolejności alfabetycznej przestrzeni nazw).

2. węzły `include` (w kolejności alfabetycznej atrybutów `schemaLocation`).

3. węzły `redefine` (w kolejności alfabetycznej atrybutów `schemaLocation`).

4. Inne węzły globalne w kolejności alfabetycznej.

### <a name="document-order"></a>Kolejność dokumentów

Opcja **kolejność dokumentów** jest dostępna po wybraniu opcji **Pokaż pliki schematu** . Po wybraniu **kolejności dokumentu** węzły globalne są wyświetlane w kolejności, w jakiej występują w pliku schematu.

## <a name="persisting-sortfilter-options"></a>Utrwalanie opcji sortowania/filtrowania

Opcje sortowania, filtrowania i grupowania są zapisywane w rejestrze dla każdego użytkownika, niezależnie od tego, które rozwiązanie lub pliki zostały otwarte, gdy ustawienia zostały zmienione.