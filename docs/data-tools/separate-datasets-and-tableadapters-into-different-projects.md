---
title: Błąd użycia oddzielnych projektów
description: Dowiedz się, jak rozdzielić zestawy danych i TableAdapters je w różne projekty, dzięki czemu możesz szybko oddzielić warstwy aplikacji i generować wielowarstwowe aplikacje do obsługi danych.
ms.date: 11/04/2016
ms.topic: how-to
ms.custom: SEO-VS-2020
helpviewer_keywords:
- TableAdapters, n-tier applications
- n-tier applications, separating Datasets and TableAdapters
ms.assetid: f66a3940-6227-46af-a930-9177f425f4fd
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 9463fe0371ee3184fd78684e7fe0565820ab3bf0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99866544"
---
# <a name="separate-datasets-and-tableadapters-into-different-projects"></a>Rozdzielanie zestawów danych i adapterów TableAdapter do różnych projektów
Wpisane zestawy danych zostały ulepszone, aby klasy [TableAdapters](create-and-configure-tableadapters.md) i DataSet mogły być generowane w oddzielnych projektach. Dzięki temu można szybko oddzielić warstwy aplikacji i generować wielowarstwowe aplikacje do obsługi danych.

Poniższa procedura opisuje proces używania **Projektant obiektów DataSet** do generowania kodu zestawu danych w projekcie, który jest oddzielony od projektu, który zawiera wygenerowany kod TableAdapter.

## <a name="separate-datasets-and-tableadapters"></a>Oddziel zestawy danych i TableAdapters
W przypadku rozdzielenia kodu zestawu danych z kodu TableAdapter, projekt zawierający kod zestawu danych musi znajdować się w bieżącym rozwiązaniu. Jeśli ten projekt nie znajduje się w bieżącym rozwiązaniu, nie będzie dostępny na liście **projektów zestawu danych** w oknie **Właściwości** .

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

#### <a name="to-separate-the-dataset-into-a-different-project"></a>Aby rozdzielić zestaw danych do innego projektu

1. Otwórz rozwiązanie, które zawiera zestaw danych (plik *XSD* ).

    > [!NOTE]
    > Jeśli rozwiązanie nie zawiera projektu, do którego chcesz oddzielić kod zestawu danych, Utwórz projekt lub Dodaj istniejący projekt do rozwiązania.

2. Kliknij dwukrotnie plik zestawu danych o określonym typie (plik *XSD* ) w **Eksplorator rozwiązań** , aby otworzyć zestaw danych w **Projektant obiektów DataSet**.

3. Wybierz pusty obszar **Projektant obiektów DataSet**.

4. W oknie **Właściwości** zlokalizuj węzeł **projektu zestawu danych** .

5. Na liście **projekt zestawu danych** wybierz nazwę projektu, do którego chcesz wygenerować kod zestawu danych.

     Po wybraniu projektu, do którego chcesz wygenerować kod zestawu danych, właściwość **pliku DataSet** zostanie wypełniona domyślną nazwą pliku. W razie potrzeby można zmienić tę nazwę. Ponadto, jeśli chcesz wygenerować kod zestawu danych w określonym katalogu, możesz ustawić właściwość **folder projektu** na nazwę folderu.

    > [!NOTE]
    > Gdy oddzielasz zestawy danych i TableAdapters (ustawiając właściwość **projektu DataSet** ), istniejące częściowe klasy zestawu danych w projekcie nie będą automatycznie przenoszone. Istniejące częściowe klasy DataSet muszą być przenoszone ręcznie do projektu DataSet.

6. Zapisz zestaw danych.

     Kod zestawu danych jest generowany w wybranym projekcie we właściwości **projektu DataSet** , a kod **TableAdapter** jest generowany w bieżącym projekcie.

Domyślnie po oddzieleniu zestawu danych i kodu TableAdapter wynik jest dyskretnym plikiem klasy w każdym projekcie. Oryginalny projekt zawiera plik o nazwie *DatasetName. Designer. vb* (lub *DatasetName.Designer.cs*), który zawiera kod TableAdapter. Projekt wskazany we właściwości **projektu DataSet** zawiera plik o nazwie *DataSetname. DataSet. Designer. vb* (lub *DatasetName.DataSet.Designer.cs*), który zawiera kod zestawu danych.

> [!NOTE]
> Aby wyświetlić wygenerowany plik klasy, wybierz projekt zestawu danych lub TableAdapter. Następnie w obszarze **Eksplorator rozwiązań** wybierz pozycję **Pokaż wszystkie pliki**.

## <a name="see-also"></a>Zobacz też

- [N-warstwowe aplikacje dotyczące danych — omówienie](../data-tools/n-tier-data-applications-overview.md)
- [Przewodnik: Tworzenie wielowarstwowej aplikacji danych](../data-tools/walkthrough-creating-an-n-tier-data-application.md)
- [Aktualizacja hierarchiczna](../data-tools/hierarchical-update.md)
- [Uzyskiwanie dostępu do danych w programie Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
- [ADO.NET](/dotnet/framework/data/adonet/index)
