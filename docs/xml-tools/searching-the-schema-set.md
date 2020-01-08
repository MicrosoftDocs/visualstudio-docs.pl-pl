---
title: Eksplorator schematu XML — przeszukiwanie zestawu schematów
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ec1395e0-d03c-4130-810d-f2db656937bd
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8378ebaccefaedfcc3d83f23bcab56f7417264dd
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75592506"
---
# <a name="search-the-schema-set"></a>Wyszukiwanie zestawu schematów

**Eksplorator schematu XML** umożliwia przeszukiwanie zestawu schematów w następujący sposób:

- Wyszukiwanie słów kluczowych.

- Wyszukiwanie specyficzne dla schematu.

## <a name="keyword-search"></a>Wyszukiwanie słów kluczowych

Wyszukiwanie słów kluczowych jest wykonywane przez wprowadzenie podciągu w polu tekstowym **Wyszukaj SchemaSet** na pasku narzędzi **Eksploratora schematu XML** .

![Wyszukiwanie słów kluczowych w Eksploratorze schematu XML](../xml-tools/media/schemaexplorersearch.gif)

**Eksplorator schematu XML** przeszukuje zestaw schematów dla następujących atrybutów:

- Wszystkie atrybuty `name` lub `ref`, które pasują do określonego słowa kluczowego. Można znaleźć elementy, atrybuty, typy i tak dalej, według nazwy.

- `schemaLocation` atrybuty instrukcji INCLUDE.

- `namespace` atrybuty instrukcji import.

## <a name="schema-specific-search"></a>Wyszukiwanie specyficzne dla schematu

**Eksplorator schematu XML** zawiera również wbudowane wyszukiwania, do których można uzyskać dostęp za pomocą menu kontekstowego (kliknij prawym przyciskiem myszy) w **Eksploratorze schematu XML**. Aby uzyskać więcej informacji na temat dostępnych menu kontekstowych, zobacz [menu kontekstowe](../xml-tools/context-menus-xml-schema-explorer.md). Możesz również wykonać wyszukiwanie specyficzne dla schematu w widoku Start. Aby uzyskać więcej informacji, zobacz sekcję "Szczegóły zestawu schematów" w temacie [Start View](../xml-tools/start-view.md) .

## <a name="display-and-navigate-search-results"></a>Wyświetlanie i nawigowanie po wynikach wyszukiwania

Po zakończeniu wyszukiwania okienko wyniki podsumowania zostanie dodane do paska narzędzi z wynikami wyszukiwania. Wyniki wyszukiwania są również wyróżnione w **Eksploratorze schematu XML** i oznaczone przez Takty na pionowym pasku przewijania. Wyniki wyszukiwania można nawigować przy użyciu przycisków **Przejdź do następnego wyszukiwania** wynik i **Przejdź do poprzedniego wyniku wyszukiwania** w okienku wyników podsumowania na pasku narzędzi **Eksploratora schematu XML** . przy użyciu klawiszy klawiatury **F3** i **SHIFT**+**F3**; lub klikając znaczniki osi na pasku przewijania.

Możesz dodać wyniki wyszukiwania do obszaru roboczego, klikając przycisk **Dodaj wyróżnione węzły do obszaru roboczego** w okienku wyników podsumowania.

![Wynik wyszukiwania Eksploratora schematu XML](../xml-tools/media/schemaexplorersearchresult.gif)

## <a name="clear-search-results"></a>Wyczyść wyniki wyszukiwania

Aby wyczyścić wyniki wyszukiwania, kliknij przycisk **x** w okienku wyników podsumowania na pasku narzędzi wyszukiwania **Eksploratora schematu XML** .

## <a name="see-also"></a>Zobacz także

- [Eksplorator schematu XML](../xml-tools/xml-schema-explorer.md)
