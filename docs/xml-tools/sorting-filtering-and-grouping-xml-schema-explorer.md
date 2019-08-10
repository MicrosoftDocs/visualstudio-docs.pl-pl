---
title: Sortowanie, filtrowanie i grupowanie w Eksploratorze schematu XML
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 4a914de0-9ffc-4526-9603-92e460e52513
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: daa629b4c26abf7b6ce801c30ea6f6fd41fbaa48
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68926729"
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

1. `import`nich.

2. `include`nich.

3. `redefine`nich.

4. `attribute`nich.

5. `attributeGroup`nich.

6. `complexType`nich.

7. `simpleType`nich.

8. `element`nich.

9. `group`nich.

### <a name="sort-by-name"></a>Sortuj według nazwy

W przypadku wybrania opcji **Sortuj według nazwy** węzły globalne są sortowane w następującej kolejności:

1. `import`węzły (w kolejności alfabetycznej przestrzeni nazw).

2. `include`węzły (w kolejności `schemaLocation` alfabetycznej atrybutów).

3. `redefine`węzły (w kolejności `schemaLocation` alfabetycznej atrybutów).

4. Inne węzły globalne w kolejności alfabetycznej.

### <a name="document-order"></a>Kolejność dokumentów

Opcja **kolejność dokumentów** jest dostępna po wybraniu opcji **Pokaż pliki schematu** . Po wybraniu **kolejności dokumentu** węzły globalne są wyświetlane w kolejności, w jakiej występują w pliku schematu.

## <a name="persisting-sortfilter-options"></a>Utrwalanie opcji sortowania/filtrowania

Opcje sortowania, filtrowania i grupowania są zapisywane w rejestrze dla każdego użytkownika, niezależnie od tego, które rozwiązanie lub pliki zostały otwarte, gdy ustawienia zostały zmienione.