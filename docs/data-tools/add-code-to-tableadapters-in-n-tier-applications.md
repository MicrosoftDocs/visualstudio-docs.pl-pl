---
title: Dodawanie kodu do adapterów TableAdapter w aplikacjach n-warstwowych
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- TableAdapters, n-tier applications
- n-tier applications, extending TableAdapters
ms.assetid: dafac00e-df9d-4d4a-95a6-e34b4d099425
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 3ea451ac60de971677ee2f7910b28b334c67dff3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85283102"
---
# <a name="add-code-to-tableadapters-in-n-tier-applications"></a>Dodawanie kodu do adapterów TableAdapter w aplikacjach n-warstwowych
Można zwiększyć funkcjonalność TableAdapter, tworząc plik klasy częściowej dla TableAdapter i dodając do niego kod (zamiast dodawać kod do pliku *DatasetName. DataSet. Designer* ). Klasy częściowe umożliwiają dzielenie kodu dla określonej klasy, aby można je było podzielić między wiele plików fizycznych. Aby uzyskać więcej informacji, zobacz [częściowe](/dotnet/visual-basic/language-reference/modifiers/partial) lub [częściowe (Type)](/dotnet/csharp/language-reference/keywords/partial-type).

Kod definiujący TableAdapter jest generowany za każdym razem, gdy zmiany są wprowadzane do TableAdapter w zestawie danych. Ten kod jest również generowany, gdy zmiany są wprowadzane podczas uruchamiania kreatora, który modyfikuje konfigurację TableAdapter. Aby zapobiec usunięciu kodu podczas ponownej generacji TableAdapter, Dodaj kod do pliku klasy częściowej TableAdapter.

Domyślnie po oddzieleniu zestawu danych i kodu TableAdapter wynik jest dyskretnym plikiem klasy w każdym projekcie. Oryginalny projekt zawiera plik o nazwie *DatasetName. Designer. vb* (lub *DatasetName.Designer.cs*), który zawiera kod TableAdapter. Projekt wskazany we właściwości **projektu DataSet** zawiera plik o nazwie *DataSetname. DataSet. Designer. vb* (lub *DatasetName.DataSet.Designer.cs*), który zawiera kod zestawu danych.

> [!NOTE]
> Gdy oddzielasz zestawy danych i TableAdapters (ustawiając właściwość **projektu DataSet** ), istniejące częściowe klasy zestawu danych w projekcie nie będą przenoszone automatycznie. Istniejące częściowe klasy DataSet muszą być przenoszone ręcznie do projektu DataSet.

> [!NOTE]
> Zestaw danych zawiera funkcje generowania <xref:System.Data.DataTable.ColumnChanging> i <xref:System.Data.DataTable.RowChanging> obsługi zdarzeń, gdy jest wymagana Walidacja. Aby uzyskać więcej informacji, zobacz [Dodawanie walidacji do wielowarstwowego zestawu danych](../data-tools/add-validation-to-an-n-tier-dataset.md).

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="to-add-user-code-to-a-tableadapter-in-an-n-tier-application"></a>Aby dodać kod użytkownika do TableAdapter w aplikacji n-warstwowej

1. Znajdź projekt, który zawiera plik *XSD* .

2. Kliknij dwukrotnie plik *XSD* , aby otworzyć **Projektant obiektów DataSet**.

3. Kliknij prawym przyciskiem myszy TableAdapter, do którego chcesz dodać kod, a następnie wybierz polecenie **Wyświetl kod**.

     Klasa częściowa jest tworzona i otwiera się w edytorze kodu.

4. Dodaj kod wewnątrz deklaracji klasy częściowej.

5. Poniższy przykład pokazuje, gdzie dodać kod do `CustomersTableAdapter` `NorthwindDataSet` :

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

- [N-warstwowe aplikacje dotyczące danych — omówienie](../data-tools/n-tier-data-applications-overview.md)
- [Dodawanie kodu do zestawów danych w aplikacjach n-warstwowych](../data-tools/add-code-to-datasets-in-n-tier-applications.md)
- [Tworzenie i konfigurowanie adapterów TableAdapter](create-and-configure-tableadapters.md)
- [Omówienie aktualizacji hierarchicznej](hierarchical-update.md)
