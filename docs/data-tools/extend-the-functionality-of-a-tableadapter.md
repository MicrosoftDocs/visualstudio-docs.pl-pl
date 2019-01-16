---
title: Rozszerzanie funkcjonalności adaptera TableAdapter
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Visual Studio], TableAdapters
- data [Visual Studio], extending TableAdapters
- TableAdapters, adding functionality
ms.assetid: 418249c8-c7f3-47ef-a94c-744cb6fe6aaf
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: 4a99ff0c28eac785e7e0e52958abcc4c94799685
ms.sourcegitcommit: 5a65ca6688a2ebb36564657d2d73c4b4f2d15c34
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2019
ms.locfileid: "53900194"
---
# <a name="extend-the-functionality-of-a-tableadapter"></a>Rozszerzanie funkcjonalności adaptera TableAdapter

Funkcjonalności TableAdapter można rozszerzyć, dodając kod do pliku częściowej klasy TableAdapter.

Wygenerowania kodu, który definiuje TableAdapter gdy zmiany zostaną wprowadzone do elementu TableAdapter w **Projektanta obiektów Dataset**, lub gdy modyfikuje przez Kreatora konfiguracji TableAdapter. Aby zapobiec usunięciu podczas ponownego generowania TableAdapter w kodzie, należy dodać kod do pliku częściowej klasy TableAdapter.

Klasy częściowe umożliwiają kod dla określonej klasy do podzielone między wiele plików fizycznych. Aby uzyskać więcej informacji, zobacz [częściowe](/dotnet/visual-basic/language-reference/modifiers/partial) lub [partial (typ)](/dotnet/csharp/language-reference/keywords/partial-type).

## <a name="locate-tableadapters-in-code"></a>Znajdź TableAdapters w kodzie

Gdy TableAdapters są skonstruowane z **Projektanta obiektów Dataset**, klasy TableAdapter, które są generowane, nie są klas zagnieżdżonych <xref:System.Data.DataSet>. TableAdapters znajdują się w przestrzeni nazw na podstawie nazwy dataset skojarzony obiekt TableAdapter. Na przykład, jeśli aplikacja zawiera zestaw danych o nazwie `HRDataSet`, elementów TableAdapter znajduje się w `HRDataSetTableAdapters` przestrzeni nazw. (Konwencji nazewnictwa tym wzorcem: *DatasetName* + `TableAdapters`).

W poniższym przykładzie założono TableAdapter o nazwie `CustomersTableAdapter`znajduje się w projekcie z `NorthwindDataSet`.

### <a name="to-create-a-partial-class-for-a-tableadapter"></a>Aby utworzyć klasę częściową dla adaptera TableAdapter

1.  Dodaj nową klasę do projektu, przechodząc do **projektu** menu i wybierając polecenie **Dodaj klasę**.

2.  Nazwa klasy `CustomersTableAdapterExtended`.

3.  Wybierz pozycję **Dodaj**.

4.  Zastąp kod poprawną przestrzeń nazw i nazwę klasy częściowej projektu w następujący sposób:

     [!code-csharp[VbRaddataTableAdapters#2](../data-tools/codesnippet/CSharp/extend-the-functionality-of-a-tableadapter_1.cs)]
     [!code-vb[VbRaddataTableAdapters#2](../data-tools/codesnippet/VisualBasic/extend-the-functionality-of-a-tableadapter_1.vb)]

## <a name="see-also"></a>Zobacz także

- [Wypełnianie zestawów danych za pomocą adapterów TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md)