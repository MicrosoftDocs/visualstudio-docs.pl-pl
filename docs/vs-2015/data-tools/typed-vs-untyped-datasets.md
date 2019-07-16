---
title: Typizowane i nietypizowane zestawy danych | Dokumentacja firmy Microsoft
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: c83ba0bb-5425-4d47-8891-6b4dbf937701
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 0d02f72a686d0f271e387e550122451db34c019a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68192776"
---
# <a name="typed-vs-untyped-datasets"></a>Typizowane i nietypizowane zestawy danych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Typizowany zestaw danych jest zestaw danych, który najpierw pochodzą od podstawy <xref:System.Data.DataSet> klasy, a następnie używa informacji z **Projektanta obiektów Dataset**, który jest przechowywany w pliku XSD, aby wygenerować nowy, silnie typizowanej klasy zestawu danych. Informacje ze schematu (tabele, kolumny i tak dalej) jest wygenerowany i kompilowane do tej nowej klasy dataset jako zbiór obiektów najwyższej klasy i właściwości. Ponieważ typizowany zestaw danych dziedziczy od podstawy <xref:System.Data.DataSet> klasy typizowanej klasy przyjęto założenie, wszystkie funkcje <xref:System.Data.DataSet> klasy i mogą być używane z metod, dla których wystąpienie <xref:System.Data.DataSet> klasy jako parametr.  
  
 Nietypizowany zestaw danych, z kolei ma odpowiedni schemat wbudowany. Jak typizowany zestaw danych jest nietypizowany zestaw danych zawiera tabele, kolumny i tak dalej, ale te są dostępne tylko jako kolekcji. (Jednak utworzony ręcznie tabele i inne elementy w nietypizowany zestaw danych, możesz wyeksportować struktury zestawu danych jako schematu przy użyciu zestawu danych <xref:System.Data.DataSet.WriteXmlSchema%2A> metody.)  
  
## <a name="contrasting-data-access-in-typed-and-untyped-datasets"></a>Kontrastujących dostęp do danych w typizowane i nietypizowane zestawy danych  
 Klasy dla typizowany zestaw danych zawiera model obiektów, które mają jej właściwości na rzeczywiste nazwy tabel i kolumn. Na przykład jeśli pracujesz z typizowany zestaw danych, możesz odwołać kolumny przy użyciu kodu, takie jak następujące:  
  
 [!code-csharp[VbRaddataDatasets#4](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDatasets/CS/Form1.cs#4)]
 [!code-vb[VbRaddataDatasets#4](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDatasets/VB/Form1.vb#4)]  
  
 Z kolei jeśli pracujesz z zestawu danych bez typu, jest równoważny kod:  
  
 [!code-csharp[VbRaddataDatasets#5](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDatasets/CS/Form1.cs#5)]
 [!code-vb[VbRaddataDatasets#5](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDatasets/VB/Form1.vb#5)]  
  
 Typizowany dostęp jest nie tylko łatwiej odczytać, ale także w pełni obsługiwane przez funkcję IntelliSense w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] **Edytor kodu**. Oprócz łatwiej pracować z, składnia typizowany zestaw danych zawiera typ sprawdzanie w czasie kompilacji, co pozwala znacznie zmniejszyć prawdopodobieństwo wystąpienia błędów podczas przypisywania wartości do elementów członkowskich zestawu danych. Jeśli zmienisz nazwę kolumny w swojej <xref:System.Data.DataSet> klasy, a następnie skompilować aplikację, zostanie wyświetlony błąd kompilacji. Klikając dwukrotnie błąd kompilacji w **listy zadań**, możesz przejść bezpośrednio do wiersz lub wiersze kodu odwołujące się do starej nazwy kolumny. Dostęp do tabel i kolumn w typizowanego zestawu danych również jest nieco szybsze, w czasie wykonywania, ponieważ dostęp jest określany w czasie kompilacji, a nie przy użyciu kolekcji w czasie wykonywania.  
  
 Mimo że typizowanych zestawów danych ma wiele zalet, nietypizowany zestaw danych jest przydatne w różnych sytuacjach. Scenariusz najbardziej oczywiste jest, gdy schemat nie jest dostępny dla zestawu danych. Taka sytuacja może wystąpić, na przykład, jeśli aplikacja prowadzi interakcję z składnik, który zwraca zestaw danych, ale nie znasz wcześniej jego struktury jest. Analogicznie istnieją razy podczas pracy z danymi, które nie ma statycznego stała, przewidywalna Struktura. W takim przypadku jest to niepraktyczne, aby użyć typizowany zestaw danych, ponieważ trzeba ponownie wygenerować klasę typizowany zestaw danych z każdej zmiany w strukturze danych.  
  
 Ogólnie rzecz biorąc są wielokrotnie podczas można dynamicznie utworzyć zestaw danych bez schematu, które są dostępne. W takim przypadku zestaw danych jest po prostu wygodne struktury zachować informacje, tak długo, jak długo dane mogą być reprezentowane w taki sposób, relacyjne. W tym samym czasie można wykorzystać możliwości zestawu danych, takich jak możliwość serializacji informacji do przekazania do innego procesu lub zapisać plik XML.
