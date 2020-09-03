---
title: Oddziel zestawy danych i TableAdapters je w różnych projektach | Microsoft Docs
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
- n-tier applications, separating Datasets and TableAdapters
ms.assetid: f66a3940-6227-46af-a930-9177f425f4fd
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6f6ec76e79cc1c4759cbe05d8bdcacc1297b655b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72655432"
---
# <a name="separate-datasets-and-tableadapters-into-different-projects"></a>Rozdzielanie zestawów danych i adapterów TableAdapter do różnych projektów
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wpisane zestawy danych zostały ulepszone, aby klasy [TableAdapters](https://msdn.microsoft.com/library/09416de9-134c-4dc7-8262-6c8d81e3f364) i DataSet mogły być generowane w oddzielnych projektach. Dzięki temu można szybko oddzielić warstwy aplikacji i generować wielowarstwowe aplikacje do obsługi danych.

 Poniższa procedura opisuje proces używania Projektant obiektów Dataset do generowania kodu zestawu danych w projekcie, który jest oddzielony od projektu, który zawiera wygenerowany `TableAdapter` kod.

## <a name="separatedatasets-and-tableadapters"></a>Separatedatasets i TableAdapters
 W przypadku rozdzielenia kodu zestawu danych od `TableAdapter` kodu projekt zawierający kod zestawu danych musi znajdować się w bieżącym rozwiązaniu. Jeśli ten projekt nie znajduje się w bieżącym rozwiązaniu, nie będzie dostępny na liście **projektów zestawu danych** w oknie **Właściwości** .

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

#### <a name="to-separate-the-dataset-into-a-different-project"></a>Aby rozdzielić zestaw danych do innego projektu

1. Otwórz rozwiązanie, które zawiera zestaw danych (plik XSD).

   > [!NOTE]
   > Jeśli rozwiązanie nie zawiera projektu, do którego chcesz oddzielić kod zestawu danych, Utwórz projekt lub Dodaj istniejący projekt do rozwiązania.

2. Kliknij dwukrotnie plik zestawu danych o określonym typie (plik XSD) w **Eksplorator rozwiązań** , aby otworzyć zestaw danych w **Projektant obiektów DataSet**.

3. Wybierz pusty obszar **Projektant obiektów DataSet**.

4. W oknie **Właściwości** zlokalizuj węzeł **projektu zestawu danych** .

5. Na liście **projekt zestawu danych** wybierz nazwę projektu, do którego chcesz wygenerować kod zestawu danych.

    Po wybraniu projektu, do którego chcesz wygenerować kod zestawu danych, właściwość **pliku DataSet** zostanie wypełniona domyślną nazwą pliku. W razie potrzeby można zmienić tę nazwę. Ponadto, jeśli chcesz wygenerować kod zestawu danych w określonym katalogu, możesz ustawić właściwość **folder projektu** na nazwę folderu.

   > [!NOTE]
   > Gdy oddzielasz zestawy danych i TableAdapters (ustawiając właściwość **projektu DataSet** ), istniejące częściowe klasy zestawu danych w projekcie nie będą automatycznie przenoszone. Istniejące klasy częściowe zestawu danych muszą być przenoszone ręcznie do projektu DataSet.

6. Zapisz zestaw danych.

    Kod zestawu danych jest generowany w wybranym projekcie we właściwości **projektu DataSet** , a kod **TableAdapter** jest generowany w bieżącym projekcie.

   Domyślnie po oddzieleniu zestawu danych i `TableAdapter` kodu wynik jest dyskretnym plikiem klasy w każdym projekcie. Oryginalny projekt zawiera plik o nazwie DatasetName. Designer. vb (lub DatasetName.Designer.cs), który zawiera `TableAdapter` kod. Projekt wskazany we właściwości **projektu DataSet** zawiera plik o nazwie DatasetName. DataSet. Designer. vb (lub DatasetName.DataSet.Designer.cs), który zawiera kod zestawu danych.

> [!NOTE]
> Aby wyświetlić wygenerowany plik klasy, wybierz zestaw danych lub `TableAdapter` projekt. Następnie w obszarze  **Eksplorator rozwiązań**wybierz pozycję **Pokaż wszystkie pliki** .

## <a name="see-also"></a>Zobacz też
 [N-warstwowe aplikacje dotyczące danych](../data-tools/n-tier-data-applications-overview.md) — wskazówki [: Tworzenie wielowarstwowej aplikacji do obsługi danych,](../data-tools/walkthrough-creating-an-n-tier-data-application.md) [Hierarchical update](../data-tools/hierarchical-update.md) [dostęp do danych w Visual Studio](../data-tools/accessing-data-in-visual-studio.md) [ADO.NET](https://msdn.microsoft.com/library/5b96ed06-9759-4966-a797-a1d5f6ee50ca)
