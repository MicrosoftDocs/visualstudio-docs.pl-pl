---
title: Wyszukiwanie zestawu schematu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: ec1395e0-d03c-4130-810d-f2db656937bd
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0e3a8563d5e2cd29c9c521761498d7ef87b7cbab
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656158"
---
# <a name="searching-the-schema-set"></a>Wyszukiwanie zestawu schematów
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Eksplorator schematu XML umożliwia przeszukiwanie zestawu schematów w następujący sposób:

- Wyszukiwanie słów kluczowych.

- Wyszukiwanie specyficzne dla schematu.

## <a name="keyword-search"></a>Wyszukiwanie słów kluczowych
 Wyszukiwanie słów kluczowych jest wykonywane przez wprowadzenie podciągu w polu tekstowym **Wyszukaj SchemaSet** na pasku narzędzi EKSPLORATORA schematu XML.

 ![Wyszukiwanie słów kluczowych w Eksploratorze schematu XML](../xml-tools/media/schemaexplorersearch.gif "SchemaExplorerSearch")

 Eksplorator schematu XML przeszukuje zestaw schematów dla następujących:

- Wszystkie atrybuty `name` lub `ref`, które pasują do określonego słowa kluczowego. Pozwala to na znalezienie elementów, atrybutów, typów i tak dalej według nazwy.

- @No__t_0 atrybuty instrukcji INCLUDE.

- @No__t_0 atrybuty instrukcji import.

## <a name="schema-specific-search"></a>Wyszukiwanie specyficzne dla schematu
 Eksplorator schematu XML zawiera również wbudowane wyszukiwania, do których można uzyskać dostęp za pomocą menu kontekstowego Eksploratora schematu XML. Aby uzyskać więcej informacji na temat dostępnych menu kontekstowych, zobacz [menu kontekstowe](../xml-tools/context-menus-xml-schema-explorer.md). Możesz również wykonać wyszukiwanie specyficzne dla schematu w widoku Start. Aby uzyskać więcej informacji, zobacz sekcję "Szczegóły zestawu schematów" w temacie [Start View](../xml-tools/start-view.md) .

## <a name="displaying-and-navigating-search-results"></a>Wyświetlanie i nawigowanie po wynikach wyszukiwania
 Po zakończeniu wyszukiwania okienko wyniki podsumowania zostanie dodane do paska narzędzi z wynikami wyszukiwania. Wyniki wyszukiwania są również wyróżnione w Eksploratorze schematu XML i oznaczone przez Takty na pionowym pasku przewijania. Wyniki wyszukiwania można nawigować przy użyciu przycisków **Przejdź do następnego wyszukiwania** wynik i **Przejdź do poprzedniego wyniku wyszukiwania** w okienku wyników podsumowania na pasku narzędzi Eksploratora schematu XML. przy użyciu klawiszy klawiatury F3 i Shift + F3; lub klikając znaczniki osi na pasku przewijania.

 Możesz dodać wyniki wyszukiwania do obszaru roboczego, klikając przycisk **Dodaj wyróżnione węzły do obszaru roboczego** w okienku wyników podsumowania.

 ![Wynik wyszukiwania Eksploratora schematu XML](../xml-tools/media/schemaexplorersearchresult.gif "SchemaExplorerSearchResult")

## <a name="clearing-search-results"></a>Czyszczenie wyników wyszukiwania
 Aby wyczyścić wyniki wyszukiwania, kliknij przycisk **x** w okienku wyników podsumowania na pasku narzędzi wyszukiwania EKSPLORATORA schematu XML.

## <a name="see-also"></a>Zobacz też
 [Eksplorator schematu XML](../xml-tools/xml-schema-explorer.md)
