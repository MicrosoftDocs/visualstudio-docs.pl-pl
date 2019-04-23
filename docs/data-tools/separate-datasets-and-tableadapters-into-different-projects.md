---
title: Rozdzielanie zestawów danych i adapterów TableAdapter do różnych projektów
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- TableAdapters, n-tier applications
- n-tier applications, separating Datasets and TableAdapters
ms.assetid: f66a3940-6227-46af-a930-9177f425f4fd
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 8a24b934b0ffe4cc22dc7be01aca19910ee3c768
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60096871"
---
# <a name="separate-datasets-and-tableadapters-into-different-projects"></a>Rozdzielanie zestawów danych i adapterów TableAdapter do różnych projektów
Typizowane zestawy danych zostały rozszerzone, aby [TableAdapters](create-and-configure-tableadapters.md) i klasy zestawu danych mogą być generowane w oddzielnych projektów. Dzięki temu można szybko oddzielnymi warstwami aplikacji i generowania aplikacji n warstwowa danych.

W poniższej procedurze opisano sposób korzystania z **Projektanta obiektów Dataset** do generowania kodu zestawu danych do projektu, który jest oddzielony od projektu, który zawiera wygenerowanego kodu TableAdapter.

## <a name="separate-datasets-and-tableadapters"></a>Rozdzielanie zestawów danych i TableAdapters
Gdy kod zestawu danych można oddzielić od kodu TableAdapter, projekt, który zawiera kod zestawu danych musi znajdować się w bieżącym rozwiązaniu. Jeśli ten projekt nie znajduje się w bieżącym rozwiązaniu, nie będzie dostępna w **projektu DataSet** listy w **właściwości** okna.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

#### <a name="to-separate-the-dataset-into-a-different-project"></a>Aby podzielić zestawu danych na inny projekt

1. Otwórz rozwiązanie, które zawiera zestaw danych (*XSD* pliku).

    > [!NOTE]
    >  Jeśli rozwiązanie zawiera projekt, do którego chcesz rozdzielić swój kod w zestawie danych, tworzenia projektu lub dodać istniejący projekt do rozwiązania.

2. Kliknij dwukrotnie plik typizowany zestaw danych ( *XSD* pliku) w **Eksploratora rozwiązań** można otworzyć zestawu danych w **Projektanta obiektów Dataset**.

3. Wybierz pusty obszar **Projektanta obiektów Dataset**.

4. W **właściwości** oknie Znajdź **projektu DataSet** węzła.

5. W **projektu DataSet** , wybierz nazwę projektu, do którego chcesz wygenerować kod zestawu danych na liście.

     Po wybraniu projektu, do którego chcesz wygenerować kod zestawu danych **plik zestawu danych** właściwość jest wypełniana przy użyciu domyślnej nazwy pliku. Jeśli to konieczne, możesz zmienić tę nazwę. Ponadto, jeśli chcesz wygenerować kod zestawu danych w określonym katalogu, można ustawić **folderu projektu** właściwość na nazwę folderu.

    > [!NOTE]
    >  Kiedy oddzielisz zestawy danych i TableAdapters (przez ustawienie **projektu DataSet** właściwości), istniejące częściowe klasy zestawu danych w projekcie nie będą przenoszone automatycznie. Istniejące klasy częściowego zestawu danych należy przenieść ręcznie do projektu zestawu danych.

6. Zapisz zestaw danych.

     Kod zestawu danych jest generowany w wybranym projekcie w **projektu DataSet** właściwości i **TableAdapter** kod jest generowany w bieżącym projekcie.

Domyślnie po oddzielić zestaw danych i kod TableAdapter wynik jest plik klasy dyskretnych w każdym projekcie. Oryginalny projekt zawiera plik o nazwie *DatasetName.Designer.vb* (lub *DatasetName.Designer.cs*) zawierający kod TableAdapter. Projekt, który jest wyznaczone w **projektu Dataset** właściwość ma w pliku o nazwie *DatasetName.DataSet.Designer.vb* (lub *DatasetName.DataSet.Designer.cs*), zawiera kod zestawu danych.

> [!NOTE]
>  Aby wyświetlić plik wygenerowanej klasy, wybierz zestaw danych lub projektu TableAdapter. Następnie w **Eksploratora rozwiązań**, wybierz opcję **Pokaż wszystkie pliki**.

## <a name="see-also"></a>Zobacz także

- [Omówienie aplikacji N-warstwowa danych](../data-tools/n-tier-data-applications-overview.md)
- [Przewodnik: Tworzenie aplikacji N-warstwowa danych](../data-tools/walkthrough-creating-an-n-tier-data-application.md)
- [Aktualizacja hierarchiczna](../data-tools/hierarchical-update.md)
- [Uzyskiwanie dostępu do danych w programie Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
- [ADO.NET](/dotnet/framework/data/adonet/index)