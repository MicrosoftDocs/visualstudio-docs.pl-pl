---
title: Rozszerzanie funkcjonalności adaptera TableAdapter
description: Dowiedz się, jak zwiększyć funkcjonalność TableAdapter przez dodanie kodu do pliku klasy częściowej TableAdapter.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Visual Studio], TableAdapters
- data [Visual Studio], extending TableAdapters
- TableAdapters, adding functionality
ms.assetid: 418249c8-c7f3-47ef-a94c-744cb6fe6aaf
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: f8cea8ec761bf50ddc0f928112975c366f62418b
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2021
ms.locfileid: "106215841"
---
# <a name="extend-the-functionality-of-a-tableadapter"></a>Rozszerzanie funkcjonalności adaptera TableAdapter

Można zwiększyć funkcjonalność TableAdapter, dodając kod do pliku klasy częściowej TableAdapter.

Kod definiujący TableAdapter jest generowany ponownie, gdy wprowadzane są zmiany do TableAdapter w **Projektant obiektów DataSet** lub Kreator modyfikuje konfigurację TableAdapter. Aby zapobiec usunięciu kodu podczas ponownej generacji TableAdapter, Dodaj kod do pliku klasy częściowej TableAdapter.

Klasy częściowe umożliwiają dzielenie kodu dla określonej klasy między wiele plików fizycznych. Aby uzyskać więcej informacji, zobacz [częściowe](/dotnet/visual-basic/language-reference/modifiers/partial) lub [częściowe (Type)](/dotnet/csharp/language-reference/keywords/partial-type).

## <a name="locate-tableadapters-in-code"></a>Znajdź TableAdapters w kodzie

Podczas gdy TableAdapters są zaprojektowane z **Projektant obiektów DataSet**, klasy TableAdapter, które są generowane, nie są klasami zagnieżdżonymi klasy <xref:System.Data.DataSet> . TableAdapters znajdują się w przestrzeni nazw na podstawie nazwy skojarzonego zestawu danych TableAdapter. Na przykład jeśli aplikacja zawiera zestaw danych o nazwie `HRDataSet` , TableAdapters będzie znajdować się w `HRDataSetTableAdapters` przestrzeni nazw. (Konwencja nazewnictwa jest zgodna z tym wzorcem: *DataSetName*  +  `TableAdapters` ).

W poniższym przykładzie założono, że TableAdapter o nazwie `CustomersTableAdapter` jest w projekcie z `NorthwindDataSet` .

### <a name="to-create-a-partial-class-for-a-tableadapter"></a>Aby utworzyć klasę częściową dla elementu TableAdapter

1. Dodaj nową klasę do projektu, przechodząc do menu **projekt** i wybierając polecenie **Dodaj klasę**.

2. Nadaj nazwę klasie `CustomersTableAdapterExtended` .

3. Wybierz pozycję **Dodaj**.

4. Zastąp kod poprawną przestrzenią nazw i częściową nazwą klasy dla projektu w następujący sposób:

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataTableAdapters/CS/CustomersTableAdapterExtended.cs" id="Snippet2":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataTableAdapters/VB/CustomersTableAdapterExtended.vb" id="Snippet2":::

## <a name="see-also"></a>Zobacz też

- [Wypełnianie zestawów danych za pomocą adapterów TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md)
