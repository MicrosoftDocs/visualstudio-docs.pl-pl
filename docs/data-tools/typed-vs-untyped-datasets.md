---
title: Typizowane i nietypizowane zestawy danych
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
ms.assetid: c83ba0bb-5425-4d47-8891-6b4dbf937701
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: eff5e0d2f13bfe462ff19d6cfb4e8a32a15a6064
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72639639"
---
# <a name="typed-vs-untyped-datasets"></a>Typizowane i nietypizowane zestawy danych
Określony zestaw danych jest zestawem danych, który najpierw pochodzi od klasy bazowej <xref:System.Data.DataSet>, a następnie używa informacji z **Projektant obiektów DataSet**, który jest przechowywany w pliku XSD, aby wygenerować nową, silnie wpisaną klasę zestawu danych. Informacje ze schematu (tabele, kolumny i tak dalej) są generowane i kompilowane w tej nowej klasie DataSet jako zestaw obiektów i właściwości pierwszej klasy. Ponieważ typ DataSet dziedziczy z klasy podstawowej <xref:System.Data.DataSet>, Klasa Type przyjmuje wszystkie funkcje klasy <xref:System.Data.DataSet> i może być używana z metodami, które pobierają wystąpienie klasy <xref:System.Data.DataSet> jako parametr.

Zestaw danych bez typu, w przeciwieństwie, nie ma odpowiedniego wbudowanego schematu. Tak jak w określonym zestawie danych, zestaw danych bez typu zawiera tabele, kolumny i tak dalej, ale te są ujawniane tylko jako kolekcje. Po ręcznym utworzeniu tabel i innych elementów danych w niewpisanym zestawie danych można wyeksportować strukturę zestawu danych jako schemat za pomocą metody <xref:System.Data.DataSet.WriteXmlSchema%2A> zestawu danych.

## <a name="contrast-data-access-in-typed-and-untyped-datasets"></a>Dostęp do danych kontrastowych typów i nieokreślonych zestawów danych
Klasa dla określonego zestawu danych ma model obiektu, w którym jego właściwości przyjmuje rzeczywiste nazwy tabel i kolumn. Na przykład jeśli pracujesz z określonym zestawem danych, możesz odwoływać się do kolumny przy użyciu kodu, takiego jak:

[!code-csharp[VbRaddataDatasets#4](../data-tools/codesnippet/CSharp/typed-vs-untyped-datasets_1.cs)]
[!code-vb[VbRaddataDatasets#4](../data-tools/codesnippet/VisualBasic/typed-vs-untyped-datasets_1.vb)]

Z drugiej strony, jeśli pracujesz z niewpisanym zestawem danych, odpowiedni kod jest:

[!code-csharp[VbRaddataDatasets#5](../data-tools/codesnippet/CSharp/typed-vs-untyped-datasets_2.cs)]
[!code-vb[VbRaddataDatasets#5](../data-tools/codesnippet/VisualBasic/typed-vs-untyped-datasets_2.vb)]

Dostęp z określonym typem nie jest łatwiejszy do odczytania, ale również w pełni obsługiwany przez funkcję IntelliSense w **edytorze kodu**programu Visual Studio. Oprócz ułatwienia pracy z programem, składnia dla określonego zestawu danych zapewnia kontrolę typu w czasie kompilacji, znacznie zmniejszając prawdopodobieństwo błędów w przypisywaniu wartości do członków zestawu danych. Jeśli zmienisz nazwę kolumny w klasie <xref:System.Data.DataSet>, a następnie kompilujesz aplikację, zostanie wyświetlony błąd kompilacji. Po dwukrotnym kliknięciu błędu kompilacji w **Lista zadań**możesz przejść bezpośrednio do linii lub wierszy kodu, który odwołuje się do starej nazwy kolumny. Dostęp do tabel i kolumn w określonym zestawie danych jest również nieco szybszy w czasie wykonywania, ponieważ dostęp jest określany w czasie kompilacji, a nie za pomocą kolekcji w czasie wykonywania.

Pomimo tego, że typy zestawów danych mają wiele zalet, nieokreślony zestaw DataSet jest przydatny w różnych sytuacjach. Najbardziej oczywistym scenariuszem jest to, że żaden schemat nie jest dostępny dla zestawu danych. Może się to zdarzyć na przykład wtedy, gdy aplikacja działa ze składnikiem, który zwraca zestaw danych, ale nie wiadomo, jak jego struktura jest. Podobnie istnieją przypadki, w których pracujesz z danymi, które nie mają statycznej struktury przewidywalnej. W takim przypadku niepraktyczne jest użycie określonego zestawu danych, ponieważ konieczne jest ponowne wygenerowanie klasy zestawu danych z każdą zmianą w strukturze danych.

Zwykle istnieje wiele przypadków, w których można utworzyć zestaw danych dynamicznie bez udostępniania schematu. W takim przypadku zestaw danych jest po prostu wygodną strukturą, w której można przechowywać informacje, o ile dane mogą być reprezentowane w sposób relacyjny. W tym samym czasie można korzystać z możliwości zestawu danych, takich jak możliwość serializacji informacji do przekazania do innego procesu lub do zapisania pliku XML.

## <a name="see-also"></a>Zobacz także

- [Narzędzia do obsługi zestawów danych](../data-tools/dataset-tools-in-visual-studio.md)