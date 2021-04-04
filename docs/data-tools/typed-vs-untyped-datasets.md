---
title: Typizowane i nietypizowane zestawy danych
description: Zapoznaj się z różnicą między wpisanymi i nietypu zestawami danych. Dostęp do danych kontrastu w typach i nietypowych zestawy danych.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
ms.assetid: c83ba0bb-5425-4d47-8891-6b4dbf937701
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: daf4f722eb51a08e7a6ddb287e5b54956ecdfe73
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2021
ms.locfileid: "106216023"
---
# <a name="typed-vs-untyped-datasets"></a>Typizowane i nietypizowane zestawy danych
Określony zestaw danych jest zestawem danych, który najpierw pochodzi od klasy bazowej, <xref:System.Data.DataSet> a następnie używa informacji z **Projektant obiektów DataSet**, który jest przechowywany w pliku XSD, aby wygenerować nową, silnie wpisaną klasę zestawu danych. Informacje ze schematu (tabele, kolumny i tak dalej) są generowane i kompilowane w tej nowej klasie DataSet jako zestaw obiektów i właściwości pierwszej klasy. Ponieważ typ DataSet dziedziczy z <xref:System.Data.DataSet> klasy bazowej, typ klasy przyjmuje wszystkie funkcje <xref:System.Data.DataSet> klasy i może być używany z metodami, które pobierają wystąpienie <xref:System.Data.DataSet> klasy jako parametr.

Zestaw danych bez typu, w przeciwieństwie, nie ma odpowiedniego wbudowanego schematu. Tak jak w określonym zestawie danych, zestaw danych bez typu zawiera tabele, kolumny i tak dalej, ale te są ujawniane tylko jako kolekcje. Po ręcznym utworzeniu tabel i innych elementów danych w nietypem zestawu danych można wyeksportować strukturę zestawu danych jako schemat przy użyciu metody zestawu danych <xref:System.Data.DataSet.WriteXmlSchema%2A> .

## <a name="contrast-data-access-in-typed-and-untyped-datasets"></a>Dostęp do danych kontrastowych typów i nieokreślonych zestawów danych
Klasa dla określonego zestawu danych ma model obiektu, w którym jego właściwości przyjmuje rzeczywiste nazwy tabel i kolumn. Na przykład jeśli pracujesz z określonym zestawem danych, możesz odwoływać się do kolumny przy użyciu kodu, takiego jak:

:::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDatasets/CS/Form1.cs" id="Snippet4":::
:::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDatasets/VB/Form1.vb" id="Snippet4":::

Z drugiej strony, jeśli pracujesz z niewpisanym zestawem danych, odpowiedni kod jest:

:::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDatasets/CS/Form1.cs" id="Snippet5":::
:::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDatasets/VB/Form1.vb" id="Snippet5":::

Dostęp z określonym typem nie jest łatwiejszy do odczytania, ale również w pełni obsługiwany przez funkcję IntelliSense w **edytorze kodu** programu Visual Studio. Oprócz ułatwienia pracy z programem, składnia dla określonego zestawu danych zapewnia kontrolę typu w czasie kompilacji, znacznie zmniejszając prawdopodobieństwo błędów w przypisywaniu wartości do członków zestawu danych. Jeśli zmienisz nazwę kolumny w <xref:System.Data.DataSet> klasie, a następnie kompilujesz aplikację, zostanie wyświetlony błąd kompilacji. Po dwukrotnym kliknięciu błędu kompilacji w **Lista zadań** możesz przejść bezpośrednio do linii lub wierszy kodu, który odwołuje się do starej nazwy kolumny. Dostęp do tabel i kolumn w określonym zestawie danych jest również nieco szybszy w czasie wykonywania, ponieważ dostęp jest określany w czasie kompilacji, a nie za pomocą kolekcji w czasie wykonywania.

Pomimo tego, że typy zestawów danych mają wiele zalet, nieokreślony zestaw DataSet jest przydatny w różnych sytuacjach. Najbardziej oczywistym scenariuszem jest to, że żaden schemat nie jest dostępny dla zestawu danych. Może się to zdarzyć na przykład wtedy, gdy aplikacja działa ze składnikiem, który zwraca zestaw danych, ale nie wiadomo, jak jego struktura jest. Podobnie istnieją przypadki, w których pracujesz z danymi, które nie mają statycznej struktury przewidywalnej. W takim przypadku niepraktyczne jest użycie określonego zestawu danych, ponieważ konieczne jest ponowne wygenerowanie klasy zestawu danych z każdą zmianą w strukturze danych.

Zwykle istnieje wiele przypadków, w których można utworzyć zestaw danych dynamicznie bez udostępniania schematu. W takim przypadku zestaw danych jest po prostu wygodną strukturą, w której można przechowywać informacje, o ile dane mogą być reprezentowane w sposób relacyjny. W tym samym czasie można korzystać z możliwości zestawu danych, takich jak możliwość serializacji informacji do przekazania do innego procesu lub do zapisania pliku XML.

## <a name="see-also"></a>Zobacz też

- [Narzędzia zestawu danych](../data-tools/dataset-tools-in-visual-studio.md)
