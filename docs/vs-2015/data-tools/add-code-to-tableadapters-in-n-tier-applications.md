---
title: Dodawanie kodu do TableAdapters w aplikacjach n-warstwowych | Microsoft Docs
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
- TableAdapters, n-tier applications
- n-tier applications, extending TableAdapters
ms.assetid: dafac00e-df9d-4d4a-95a6-e34b4d099425
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 942850e776cdd493afaad56b782b417db2040625
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72673100"
---
# <a name="add-code-to-tableadapters-in-n-tier-applications"></a>Dodawanie kodu do adapterów TableAdapter w aplikacjach n-warstwowych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Można zwiększyć funkcjonalność `TableAdapter`, tworząc plik klasy częściowej dla `TableAdapter` i dodając do niego kod (zamiast dodawać kod do *zestawu danychname*. Plik DataSet. Designer). Klasy częściowe umożliwiają dzielenie kodu dla określonej klasy, aby można je było podzielić między wiele plików fizycznych. Aby uzyskać więcej informacji, zobacz [częściowe](https://msdn.microsoft.com/library/7adaef80-f435-46e1-970a-269fff63b448) lub [częściowe (Type)](https://msdn.microsoft.com/library/27320743-a22e-4c7b-b0b3-53afe3607334).

 Kod definiujący `TableAdapter` jest generowany za każdym razem, gdy wprowadzane są zmiany w `TableAdapter`. Ten kod jest również generowany, gdy wprowadzane są zmiany w trakcie działania kreatora, który modyfikuje konfigurację `TableAdapter`. Aby zapobiec usunięciu kodu podczas ponownej generacji `TableAdapter`, Dodaj kod do pliku klasy częściowej `TableAdapter`.

 Domyślnie po rozdzieleniu zestawu danych i kodu `TableAdapter` wynik jest dyskretnym plikiem klasy w każdym projekcie. Oryginalny projekt ma plik o nazwie *DataSetName*. Designer. vb (lub *DataSetName*. Designer.cs), który zawiera kod `TableAdapter`. Projekt, który jest wskazany we właściwości **projektu DataSet** , ma plik o nazwie *DataSetName*. DataSet. Designer. vb (lub *DataSetName*. DataSet.Designer.cs), który zawiera kod zestawu danych.

> [!NOTE]
> W przypadku rozdzielania zestawów danych i `TableAdapter`s (przez ustawienie właściwości **projektu DataSet** ) istniejące częściowe klasy zestawu danych w projekcie nie będą automatycznie przenoszone. Istniejące klasy częściowe zestawu danych muszą być przenoszone ręcznie do projektu DataSet.

> [!NOTE]
> Projektant obiektów DataSet udostępnia funkcje generowania <xref:System.Data.DataTable.ColumnChanging> i <xref:System.Data.DataTable.RowChanging> obsługi zdarzeń, gdy jest wymagana Walidacja. Aby uzyskać więcej informacji, zobacz [Dodawanie walidacji do wielowarstwowego zestawu danych](../data-tools/add-validation-to-an-n-tier-dataset.md).

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

### <a name="to-add-user-code-to-a-tableadapter-in-an-n-tier-application"></a>Aby dodać kod użytkownika do TableAdapter w aplikacji n-warstwowej

1. Znajdź projekt, który zawiera plik XSD (DataSet).

2. Kliknij dwukrotnie plik **XSD** , aby otworzyć zestaw danych.

3. Kliknij prawym przyciskiem myszy `TableAdapter`, do której chcesz dodać kod, a następnie wybierz polecenie**Wyświetl kod**.

     Klasa częściowa jest tworzona i otwiera się w edytorze kodu.

4. Dodaj kod wewnątrz deklaracji klasy częściowej.

5. Poniższy przykład pokazuje, gdzie dodać kod do `CustomersTableAdapter` w `NorthwindDataSet`:

    ```vb
    Partial Public Class CustomersTableAdapter
        ' Add code here to add functionality
        ' to the CustomersTableAdapter.
    End Class
    ```

    ```csharp
    public partial class CustomersTableAdapter
    {
        // Add code here to add functionality
        // to the CustomersTableAdapter.
    }
    ```

## <a name="see-also"></a>Zobacz też
 [N-warstwowe aplikacje dotyczące danych — omówienie](../data-tools/n-tier-data-applications-overview.md) [Dodawanie kodu do zestawów DataSet w aplikacjach N-warstwowych](../data-tools/add-code-to-datasets-in-n-tier-applications.md) [TableAdapters](https://msdn.microsoft.com/library/09416de9-134c-4dc7-8262-6c8d81e3f364) [TableAdapterManager Omówienie](https://msdn.microsoft.com/library/33076d42-6b41-491a-ac11-6c6339aea650) [hierarchicznej aktualizacji](https://msdn.microsoft.com/library/c4f8e8b9-e4a5-4a02-8462-d03d1e8222d6)