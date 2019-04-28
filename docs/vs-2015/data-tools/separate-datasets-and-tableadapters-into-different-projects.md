---
title: Oddzielanie zestawów danych i TableAdapters do różnych projektów | Dokumentacja firmy Microsoft
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: c90943f64166cfd5113032d14c2c66be1db858eb
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63425095"
---
# <a name="separate-datasets-and-tableadapters-into-different-projects"></a>Rozdzielanie zestawów danych i adapterów TableAdapter do różnych projektów
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Typizowane zestawy danych zostały rozszerzone, aby [TableAdapters](http://msdn.microsoft.com/library/09416de9-134c-4dc7-8262-6c8d81e3f364) i klasy zestawu danych mogą być generowane w oddzielnych projektów. Dzięki temu można szybko oddzielnymi warstwami aplikacji i generowania aplikacji n warstwowa danych.  
  
 W poniższej procedurze opisano proces za pomocą Projektanta obiektów Dataset, aby wygenerować kod zestawu danych do projektu, który jest oddzielony od projektu, który zawiera wygenerowaną `TableAdapter` kodu.  
  
## <a name="separatedatasets-and-tableadapters"></a>Separatedatasets i TableAdapters  
 Kiedy oddzielisz kodu zestawu danych z `TableAdapter` kodu, projekt, który zawiera kod zestawu danych musi znajdować się w bieżącym rozwiązaniu. Jeśli ten projekt nie znajduje się w bieżącym rozwiązaniu, nie będzie dostępna w **projektu DataSet** listy w **właściwości** okna.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
#### <a name="to-separate-the-dataset-into-a-different-project"></a>Aby podzielić zestawu danych na inny projekt  
  
1. Otwórz rozwiązanie, które zawiera zestaw danych (plik XSD).  
  
   > [!NOTE]
   > Jeśli rozwiązanie zawiera projekt, do którego chcesz rozdzielić swój kod w zestawie danych, tworzenia projektu lub dodać istniejący projekt do rozwiązania.  
  
2. Kliknij dwukrotnie plik typizowany zestaw danych (plik XSD) **Eksploratora rozwiązań** można otworzyć zestawu danych w **Projektanta obiektów Dataset**.  
  
3. Wybierz pusty obszar **Projektanta obiektów Dataset**.  
  
4. W **właściwości** oknie Znajdź **projektu DataSet** węzła.  
  
5. W **projektu DataSet** , wybierz nazwę projektu, do którego chcesz wygenerować kod zestawu danych na liście.  
  
    Po wybraniu projektu, do którego chcesz wygenerować kod zestawu danych **plik zestawu danych** właściwość jest wypełniana przy użyciu domyślnej nazwy pliku. Jeśli to konieczne, możesz zmienić tę nazwę. Ponadto, jeśli chcesz wygenerować kod zestawu danych w określonym katalogu, można ustawić **folderu projektu** właściwość na nazwę folderu.  
  
   > [!NOTE]
   > Kiedy oddzielisz zestawy danych i TableAdapters (przez ustawienie **projektu DataSet** właściwości), istniejące częściowe klasy zestawu danych w projekcie nie będą przenoszone automatycznie. Istniejące klasy częściowego zestawu danych należy przenieść ręcznie do projektu zestawu danych.  
  
6. Zapisz zestaw danych.  
  
    Kod zestawu danych jest generowany w wybranym projekcie w **projektu DataSet** właściwości i **TableAdapter** kod jest generowany w bieżącym projekcie.  
  
   Domyślnie po rozdzielenie zestawu danych i `TableAdapter` kod, wynik jest plik klasy dyskretnych w każdym projekcie. Oryginalny projekt zawiera plik o nazwie DatasetName.Designer.vb (lub DatasetName.Designer.cs) zawierający `TableAdapter` kodu. Projekt, który jest wyznaczone w **projektu Dataset** właściwość zawiera plik o nazwie DatasetName.DataSet.Designer.vb (lub DatasetName.DataSet.Designer.cs) zawierający kod zestawu danych.  
  
> [!NOTE]
> Aby wyświetlić plik wygenerowanej klasy, wybierz zestaw danych lub `TableAdapter` projektu. Następnie w **Eksploratora rozwiązań**, wybierz opcję **Pokaż wszystkie pliki** .  
  
## <a name="see-also"></a>Zobacz też  
 [Omówienie aplikacji N-warstwowa danych](../data-tools/n-tier-data-applications-overview.md)   
 [Przewodnik: Tworzenie aplikacji warstwowych](../data-tools/walkthrough-creating-an-n-tier-data-application.md)   
 [Hierarchiczna aktualizacja](../data-tools/hierarchical-update.md)   
 [Uzyskiwanie dostępu do danych w programie Visual Studio](../data-tools/accessing-data-in-visual-studio.md)   
 [ADO.NET](http://msdn.microsoft.com/library/5b96ed06-9759-4966-a797-a1d5f6ee50ca)
