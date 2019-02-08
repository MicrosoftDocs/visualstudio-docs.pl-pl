---
title: Eksplorator schematu XML - wyszukiwanie zestawu schematów
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ec1395e0-d03c-4130-810d-f2db656937bd
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dfbc41b24dd0e58dd24e0af99afe458d27f8ade6
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55930860"
---
# <a name="search-the-schema-set"></a>Wyszukiwanie zestawu schematów

**Eksploratora schematu XML** umożliwia wyszukiwanie schematu ustawiony w następujący sposób:

-   Wyszukiwanie słów kluczowych.

-   Wyszukiwanie specyficzne dla schematu.

## <a name="keyword-search"></a>Wyszukiwanie słów kluczowych

 Wyszukiwanie słów kluczowych, wprowadzając podciągu w **SchemaSet wyszukiwania** polu tekstowym **Eksploratora schematu XML** paska narzędzi.

 ![Wyszukiwanie słów kluczowych Eksploratora schematu XML](../xml-tools/media/schemaexplorersearch.gif)

 **Eksploratora schematu XML** wyszukuje schematu dla następujących atrybutów:

-   Wszelkie `name` lub `ref` atrybuty, które pasują do określonego słowa kluczowego. Według nazwy, można znaleźć elementy, atrybuty, typy i tak dalej.

-   `schemaLocation` Atrybuty instrukcji #include.

-   `namespace` Atrybuty instrukcje importowania.

## <a name="schema-specific-search"></a>Wyszukiwanie określonego schematu

 **Eksploratora schematu XML** zawiera także wbudowaną wyszukiwania, które mogą uzyskać dostęp za pomocą menu kontekstowe (kliknij prawym przyciskiem myszy) **Eksploratora schematu XML**. Aby uzyskać więcej informacji na temat menu kontekstowe dostępne zobacz [menu kontekstowe](../xml-tools/context-menus-xml-schema-explorer.md). Można również wykonać wyszukiwanie specyficzne dla schematu z widoku startowego; Aby uzyskać więcej informacji, zobacz sekcję "Szczegóły zestawu schematów" w [widoku Start](../xml-tools/start-view.md) tematu.

## <a name="display-and-navigate-search-results"></a>Wyświetlaj i nawigować po wynikach wyszukiwania

 Po zakończeniu wyszukiwania w okienku wyników podsumowania jest dodawany do paska narzędzi z wynikami wyszukiwania. Wyniki wyszukiwania są wyróżnione **Eksploratora schematu XML** i oznaczone przez znaczniki na pionowy pasek przewijania. Wyniki wyszukiwania można nawigować przy użyciu **przejdź do następnego wyniku wyszukiwania** i **przejdź do poprzedniego wyniku wyszukiwania** przycisków w okienku wyników podsumowania **Eksploratora schematu XML**narzędzi; za pomocą klawiszy **F3** i **Shift**+**F3**; lub klikając znaczniki na pasku przewijania.

 Wyniki wyszukiwania można dodać do obszaru roboczego, klikając **Dodaj wyróżnione węzły do obszaru roboczego** przycisk w okienku wyników podsumowania.

 ![Wynik wyszukiwania Eksploratora schematu XML](../xml-tools/media/schemaexplorersearchresult.gif)

## <a name="clear-search-results"></a>Wyczyść wyniki wyszukiwania

 Aby wyczyścić wyniki wyszukiwania, kliknij pozycję **x** przycisku w okienku wyników podsumowania **Eksploratora schematu XML** pasek narzędzi wyszukiwania.

## <a name="see-also"></a>Zobacz także

- [Eksplorator schematu XML](../xml-tools/xml-schema-explorer.md)