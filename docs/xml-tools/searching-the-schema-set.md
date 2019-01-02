---
title: Eksplorator schematu XML - wyszukiwanie zestawu schematów
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: ec1395e0-d03c-4130-810d-f2db656937bd
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 26be8121c679cc2614440f8e28f52b383dbe944c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53836572"
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

 **Eksploratora schematu XML** zawiera także wbudowaną wyszukiwania, które mogą uzyskać dostęp za pomocą menu kontekstowego **Eksploratora schematu XML**. Aby uzyskać więcej informacji na temat menu kontekstowe dostępne zobacz [menu kontekstowe](../xml-tools/context-menus-xml-schema-explorer.md). Można również wykonać wyszukiwanie specyficzne dla schematu z widoku startowego; Aby uzyskać więcej informacji, zobacz sekcję "Szczegóły zestawu schematów" w [widoku Start](../xml-tools/start-view.md) tematu.

## <a name="display-and-navigate-search-results"></a>Wyświetlaj i nawigować po wynikach wyszukiwania

 Po zakończeniu wyszukiwania w okienku wyników podsumowania jest dodawany do paska narzędzi z wynikami wyszukiwania. Wyniki wyszukiwania są wyróżnione **Eksploratora schematu XML** i oznaczone przez znaczniki na pionowy pasek przewijania. Wyniki wyszukiwania można nawigować przy użyciu **przejdź do następnego wyniku wyszukiwania** i **przejdź do poprzedniego wyniku wyszukiwania** przycisków w okienku wyników podsumowania **Eksploratora schematu XML**narzędzi; za pomocą klawiszy **F3** i **Shift**+**F3**; lub klikając znaczniki na pasku przewijania.

 Wyniki wyszukiwania można dodać do obszaru roboczego, klikając **Dodaj wyróżnione węzły do obszaru roboczego** przycisk w okienku wyników podsumowania.

 ![Wynik wyszukiwania Eksploratora schematu XML](../xml-tools/media/schemaexplorersearchresult.gif)

## <a name="clear-search-results"></a>Wyczyść wyniki wyszukiwania

 Aby wyczyścić wyniki wyszukiwania, kliknij pozycję **x** przycisku w okienku wyników podsumowania **Eksploratora schematu XML** pasek narzędzi wyszukiwania.

## <a name="see-also"></a>Zobacz także

- [Eksplorator schematu XML](../xml-tools/xml-schema-explorer.md)