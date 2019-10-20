---
title: Zwiększ funkcjonalność elementu TableAdapter | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data [Visual Studio], TableAdapters
- data [Visual Studio], extending TableAdapters
- TableAdapters, adding functionality
ms.assetid: 418249c8-c7f3-47ef-a94c-744cb6fe6aaf
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 19367f812a87d6aa585e123100f1d08144c57ff9
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672363"
---
# <a name="extend-the-functionality-of-a-tableadapter"></a>Rozszerzanie funkcjonalności adaptera TableAdapter
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Można zwiększyć funkcjonalność TableAdapter, dodając kod do pliku klasy częściowej TableAdapter.

 Kod definiujący TableAdapter jest generowany ponownie, gdy wprowadzane są zmiany do TableAdapter w **Projektant obiektów DataSet**lub Kreator modyfikuje konfigurację TableAdapter. Aby zapobiec usunięciu kodu podczas ponownej generacji TableAdapter, Dodaj kod do pliku klasy częściowej TableAdapter.

 Klasy częściowe umożliwiają dzielenie kodu dla określonej klasy między wiele plików fizycznych. Aby uzyskać więcej informacji, zobacz [częściowe](https://msdn.microsoft.com/library/7adaef80-f435-46e1-970a-269fff63b448) lub [częściowe (Type)](https://msdn.microsoft.com/library/27320743-a22e-4c7b-b0b3-53afe3607334).

## <a name="locate-tableadapters-in-code"></a>Znajdź TableAdapters w kodzie
 Chociaż TableAdapters są zaprojektowane z **Projektant obiektów DataSet**, generowane klasy TableAdapter nie są zagnieżdżonymi klasami <xref:System.Data.DataSet>. TableAdapters znajdują się w przestrzeni nazw na podstawie nazwy skojarzonego zestawu danych TableAdapter. Na przykład jeśli aplikacja zawiera zestaw danych o nazwie `HRDataSet`, TableAdapters będzie znajdować się w przestrzeni nazw `HRDataSetTableAdapters`. (Konwencja nazewnictwa jest zgodna z tym wzorcem: *datasetname*  +  `TableAdapters`).

 W poniższym przykładzie założono TableAdapter o nazwie `CustomersTableAdapter`is w projekcie z `NorthwindDataSet`.

#### <a name="to-create-a-partial-class-for-a-tableadapter"></a>Aby utworzyć klasę częściową dla elementu TableAdapter

1. Dodaj nową klasę do projektu, przechodząc do menu **projekt** i wybierając polecenie**Dodaj klasę**.

2. Nadaj klasie nazwę `CustomersTableAdapterExtended`.

3. Wybierz pozycję **Dodaj**.

4. Zastąp kod poprawną przestrzenią nazw i częściową nazwą klasy dla projektu w następujący sposób:

     [!code-csharp[VbRaddataTableAdapters#2](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataTableAdapters/CS/CustomersTableAdapterExtended.cs#2)]
     [!code-vb[VbRaddataTableAdapters#2](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataTableAdapters/VB/CustomersTableAdapterExtended.vb#2)]

## <a name="see-also"></a>Zobacz też
 [Wypełnianie zestawów danych za pomocą adapterów TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md)
