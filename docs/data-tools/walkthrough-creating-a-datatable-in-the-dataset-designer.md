---
title: 'Przewodnik: Tworzenie elementu DataTable w Projektancie obiektów Dataset'
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- DataTable objects, creating
- Dataset Designer, creating data tables
- tables [Visual Studio], creating
- data [Visual Studio], Dataset Designer
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 1126117cb1fc26c4f61bfb0f6ed0e19e86ce9323
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62564925"
---
# <a name="walkthrough-create-a-datatable-in-the-dataset-designer"></a>Przewodnik: Tworzenie obiektu DataTable w Projektancie obiektów Dataset

W tym przewodniku opisano sposób tworzenia <xref:System.Data.DataTable> (bez TableAdapter) przy użyciu **Projektanta obiektów Dataset**. Aby uzyskać informacje na temat tworzenia tabel danych, które obejmują TableAdapters, zobacz [tworzenie i konfigurowanie adapterów TableAdapter](../data-tools/create-and-configure-tableadapters.md).

## <a name="create-a-new-windows-forms-application"></a>Tworzenie nowej aplikacji Windows Forms

1. W programie Visual Studio na **pliku** menu, wybierz opcję **New** > **projektu**.

2. Rozwiń **Visual C#** lub **języka Visual Basic** w okienku po lewej stronie, a następnie zaznacz **pulpitu Windows**.

3. W środkowym okienku wybierz **Windows Forms App** typ projektu.

4. Nadaj projektowi nazwę **DataTableWalkthrough**, a następnie wybierz **OK**.

     **DataTableWalkthrough** projekt zostanie utworzony i dodany do **Eksploratora rozwiązań**.

## <a name="add-a-new-dataset-to-the-application"></a>Dodaj nowy zestaw danych do aplikacji

1. Na **projektu** menu, wybierz opcję **Dodaj nowy element**.

     **Dodaj nowy element** pojawi się okno dialogowe.

2. W okienku po lewej stronie wybierz **danych**, a następnie wybierz **DataSet** w środkowym okienku.

3. Wybierz **Dodaj**.

     Program Visual Studio dodaje plik o nazwie **DataSet1.xsd** w projekcie i otwiera go w **Projektanta obiektów Dataset**.

## <a name="add-a-new-datatable-to-the-dataset"></a>Dodaj nową tabelę DataTable do zestawu danych

1. Przeciągnij **DataTable** z **DataSet** karcie **przybornika** na **Projektanta obiektów Dataset**.

     Tabela o nazwie **DataTable1** zostanie dodany do zestawu danych.

2. Kliknij pasek tytułu **DataTable1** i zmień jego nazwę `Music`.

## <a name="add-columns-to-the-datatable"></a>Dodawanie kolumn do DataTable

1. Kliknij prawym przyciskiem myszy **utworów muzycznych** tabeli. Wskaż **Dodaj**, a następnie kliknij przycisk **kolumny**.

2. Nadaj kolumnie nazwę `SongID`.

3. W oknie **Właściwości** ustaw właściwość <xref:System.Data.DataColumn.DataType%2A> na <xref:System.Int16?displayProperty=fullName>. 

4. Powtórz ten proces i dodaj następujące kolumny:

     `SongTitle`: <xref:System.String?displayProperty=fullName>

     `Artist`: <xref:System.String?displayProperty=fullName>

     `Genre`: <xref:System.String?displayProperty=fullName>

## <a name="set-the-primary-key-for-the-table"></a>Ustaw klucz podstawowy dla tabeli

Wszystkie tabele danych powinny mieć klucz podstawowy. Klucz podstawowy jednoznacznie identyfikuje określonego rekordu w tabeli danych.

Można ustawić klucza podstawowego, kliknij prawym przyciskiem myszy **SongID** kolumny, a następnie kliknij **Ustaw klucz podstawowy**. Ikona klucza pojawia się obok **SongID** kolumny.

## <a name="save-your-project"></a>Zapisz projekt

Aby zapisać **DataTableWalkthrough** projektu na **pliku** menu, wybierz opcję **Zapisz wszystko**.

## <a name="see-also"></a>Zobacz także

- [Tworzenie i konfigurowanie zestawów danych w programie Visual Studio](../data-tools/create-and-configure-datasets-in-visual-studio.md)
- [Wiązanie kontrolek z danymi w programie Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
- [Sprawdzanie poprawności danych](../data-tools/validate-data-in-datasets.md)