---
title: Powiązanie danych WPF za pomocą omówienia LINQ to XML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 3bf80845-891b-41de-a71b-4080b5bd3ea6
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c0cbd93f2d32c06ba52b2c47c1af8f326948609a
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2020
ms.locfileid: "75843929"
---
# <a name="wpf-data-binding-with-linq-to-xml-overview"></a>Powiązanie danych WPF za pomocą LINQ to XML — omówienie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym temacie wprowadzono funkcje dynamicznego powiązania danych w przestrzeni nazw <xref:System.Xml.Linq>. Te funkcje mogą być używane jako źródło danych dla elementów interfejsu użytkownika w Windows Presentation Foundation (WPF).

## <a name="xaml-and-linq-to-xml"></a>XAML i LINQ to XML
 Extensible Application Markup Language (XAML) to dialekt XML utworzony przez firmę Microsoft do obsługi technologii .NET Framework 3,0. Jest on używany w WPF do reprezentowania elementów interfejsu użytkownika i powiązanych funkcji, takich jak zdarzenia i powiązania danych. W Windows Workflow Foundation język XAML jest używany do reprezentowania struktury programu, takiej jak sterowanie programem (*przepływy pracy*). Język XAML umożliwia rozdzielenie deklaratywnych aspektów technologicznych od powiązanego kodu proceduralnego, który definiuje bardziej indywidualne zachowanie programu.

 Istnieją dwa szerokie metody, które mogą współistnieć w języku XAML i LINQ to XML:

- Ponieważ pliki XAML są poprawnie sformułowanymi danymi XML, można je badać i manipulować nimi za poorednictwem technologii XML, takich jak LINQ to XML.

- Ponieważ zapytania LINQ to XML reprezentują źródło danych, te zapytania mogą służyć jako źródło danych dla powiązania danych dla elementów interfejsu użytkownika WPF.

  W tej dokumentacji opisano drugi scenariusz.

## <a name="data-binding-in-the-windows-presentation-foundation"></a>Powiązanie danych w Windows Presentation Foundation
 Powiązanie danych WPF umożliwia elementowi interfejsu użytkownika kojarzenie jednej z właściwości ze źródłem danych. Prostym przykładem jest <xref:System.Windows.Controls.Label>, którego tekst przedstawia wartość właściwości publicznej w obiekcie zdefiniowanym przez użytkownika. Powiązanie danych WPF opiera się na następujących składnikach:

|Składnik|Opis|
|---------------|-----------------|
|Obiekt docelowy powiązania|Element interfejsu użytkownika, który ma zostać skojarzony ze źródłem danych. Elementy wizualne w WPF pochodzą od klasy <xref:System.Windows.UIElement>.|
|Target — właściwość|*Właściwość zależności* obiektu docelowego powiązania, która odzwierciedla wartość źródła powiązań danych. Właściwości zależności są bezpośrednio obsługiwane przez klasę <xref:System.Windows.DependencyObject>, która <xref:System.Windows.UIElement> pochodzi od.|
|Źródło powiązania|Obiekt źródłowy dla co najmniej jednej wartości, która jest dostarczana do elementu interfejsu użytkownika dla prezentacji. WPF automatycznie obsługuje następujące typy jako źródła powiązań: obiekty CLR, obiekty danych ADO.NET, dane XML (z zapytań XPath lub LINQ to XML) lub inne <xref:System.Windows.DependencyObject>.|
|Ścieżka źródłowa|Właściwość źródła powiązania, która jest rozpoznawana jako wartość lub zbiór wartości, które mają być powiązane.|

 Właściwość zależności jest koncepcją specyficzną dla WPF, która reprezentuje dynamiczną obliczaną właściwość elementu interfejsu użytkownika. Na przykład właściwości zależności często mają wartości domyślne lub wartości, które są dostarczane przez element nadrzędny. Te właściwości specjalne są obsługiwane przez wystąpienia klasy <xref:System.Windows.DependencyProperty> (a nie pola z właściwościami standardowymi). Aby uzyskać więcej informacji, zobacz [Omówienie właściwości zależności](https://msdn.microsoft.com/library/d119d00c-3afb-48d6-87a0-c4da4f83dee5).

### <a name="dynamic-data-binding-in-wpf"></a>Dynamiczne powiązanie danych w WPF
 Domyślnie powiązanie danych występuje tylko wtedy, gdy docelowy element interfejsu użytkownika jest zainicjowany. Ta nazwa jest nazywana *jednorazowym* wiązaniem. W większości przypadków jest to niewystarczające. zwykle rozwiązanie do powiązania danych wymaga dynamicznego rozpropagowania zmian w czasie wykonywania przy użyciu jednego z następujących elementów:

- Powiązanie *jednokierunkowe* powoduje automatyczne propagowanie zmian w jednej stronie. Najczęściej zmiany w źródle są odzwierciedlane w elemencie docelowym, ale czasami może być przydatne.

- W przypadku powiązań *dwukierunkowych* zmiany w źródle są automatycznie propagowane do obiektu docelowego, a zmiany w obiekcie docelowym są automatycznie propagowane do źródła.

  W przypadku powiązań jednokierunkowych lub dwukierunkowych Źródło musi implementować mechanizm powiadamiania o zmianach, na przykład przez implementację interfejsu <xref:System.ComponentModel.INotifyPropertyChanged> lub przy użyciu wzorca *PropertyNameChanged* dla każdej obsługiwanej właściwości.

  Aby uzyskać więcej informacji na temat powiązania danych w WPF, zobacz [powiązanie danych (WPF)](https://msdn.microsoft.com/library/90f79b97-17e7-40d1-abf0-3ba600ad1d7e).

## <a name="dynamic-properties-in-linq-to-xml-classes"></a>Właściwości dynamiczne w klasach LINQ to XML
 Większość klas LINQ to XML nie kwalifikuje się do prawidłowych dynamicznych źródeł danych WPF: niektóre z najbardziej przydatnych informacji są dostępne tylko za pomocą metod (a nie właściwości), a właściwości w tych klasach nie implementują powiadomień o zmianach. Aby zapewnić obsługę powiązania danych WPF, LINQ to XML uwidacznia zestaw *właściwości dynamicznych*.

 Te właściwości dynamiczne są specjalnymi właściwościami czasu wykonywania, które duplikują funkcje istniejących metod i właściwości w klasach <xref:System.Xml.Linq.XAttribute> i <xref:System.Xml.Linq.XElement>. Zostały dodane do tych klas wyłącznie w celu umożliwienia im działania jako dynamiczne źródła danych dla WPF. Aby spełnić to wymaganie, wszystkie te właściwości dynamiczne implementują powiadomienia o zmianach. Szczegółowe informacje o tych właściwościach dynamicznych znajdują się w następnej sekcji [LINQ to XML właściwości dynamiczne](../designers/linq-to-xml-dynamic-properties.md).

> [!NOTE]
> Wiele standardowych właściwości publicznych, które znajdują się w różnych klasach w przestrzeni nazw <xref:System.Xml.Linq>, może być używany do jednorazowego wiązania danych. Należy jednak pamiętać, że żadne Źródło ani obiekt docelowy nie będą aktualizowane dynamicznie w ramach tego schematu.

### <a name="accessing-dynamic-properties"></a>Uzyskiwanie dostępu do właściwości dynamicznych
 Nie można uzyskać dostępu do właściwości dynamicznych z klas <xref:System.Xml.Linq.XAttribute> i <xref:System.Xml.Linq.XElement>, takich jak właściwości standardowe. Na przykład w przypadku języków zgodnych ze środowiskiem C#CLR takie jak nie mogą być:

- Dostępne bezpośrednio w czasie kompilacji. Właściwości dynamiczne są niewidoczne dla kompilatora i programu Visual Studio IntelliSense.

- Odnalezione lub dostępne w czasie wykonywania przy użyciu odbicia platformy .NET. Nawet w czasie wykonywania nie są właściwościami w podstawowym sensie CLR.

  W C#programie właściwości dynamiczne są dostępne tylko w czasie wykonywania za pomocą obiektów dostarczonych przez przestrzeń nazw <xref:System.ComponentModel>.

  Natomiast w przypadku właściwości dynamicznych źródła XML można uzyskać dostęp za pomocą prostej notacji w następującej postaci:

```
<object>.<dynamic-property>
```

 Właściwości dynamiczne tych dwóch klas są rozpoznawane jako wartość, która może być używana bezpośrednio lub do indeksatora, który musi być dostarczony z indeksem w celu uzyskania wartości lub kolekcji wartości. Ostatnia składnia przyjmuje postać:

```
<object>.<dynamic-property>[<index-value>]
```

 Aby uzyskać więcej informacji, zobacz [LINQ to XML właściwości dynamiczne](../designers/linq-to-xml-dynamic-properties.md).

 Aby zaimplementować dynamiczne powiązanie WPF, właściwości dynamiczne będą używane z obiektami dostarczanymi przez przestrzeń nazw <xref:System.Windows.Data>, w szczególności dla klasy <xref:System.Windows.Data.Binding>.

## <a name="see-also"></a>Zobacz też
 [Powiązanie danych WPF z LINQ to XML](../designers/wpf-data-binding-with-linq-to-xml.md) [LINQ to XML właściwości dynamiczne](../designers/linq-to-xml-dynamic-properties.md) [XAML w](https://msdn.microsoft.com/library/5d858575-a83b-42df-ad3f-047ed2d6e3c8) [powiązaniu danych WPF (WPF)](https://msdn.microsoft.com/library/90f79b97-17e7-40d1-abf0-3ba600ad1d7e) [przy użyciu znaczników przepływu pracy](https://msdn2.microsoft.com/library/ms735921(vs.90).aspx)
