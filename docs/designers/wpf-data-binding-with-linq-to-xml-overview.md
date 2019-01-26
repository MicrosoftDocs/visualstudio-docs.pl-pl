---
title: Powiązanie danych WPF za pomocą LINQ to XML — Przegląd
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: 3bf80845-891b-41de-a71b-4080b5bd3ea6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: da32989ebabb4ef6507f45c652755514f4963ef6
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54984785"
---
# <a name="wpf-data-binding-with-linq-to-xml-overview"></a>Powiązanie danych WPF za pomocą LINQ to XML — Przegląd

W tym temacie przedstawiono funkcje powiązania danych dynamicznych w <xref:System.Xml.Linq> przestrzeni nazw. Te funkcje może służyć jako źródło danych dla elementów interfejsu użytkownika w aplikacjach Windows Presentation Foundation (WPF). W tym scenariuszu opiera się na specjalne *właściwości dynamicznych* z <xref:System.Xml.Linq.XAttribute?displayProperty=fullName> i <xref:System.Xml.Linq.XElement?displayProperty=fullName>.

## <a name="xaml-and-linq-to-xml"></a>XAML i LINQ to XML

Extensible Application Markup Language (XAML) jest dialekt XML utworzone przez firmę Microsoft do obsługi technologii .NET Framework 3.0. Używane na platformie WPF reprezentujące elementy interfejsu użytkownika i powiązane funkcje, takie jak zdarzenia i powiązanie danych. W programie Windows Workflow Foundation XAML jest używana do reprezentowania struktury programów, takich jak formant programu (*przepływy pracy*). XAML umożliwia deklaratywne aspektów technologii od powiązany kod proceduralny definiujący bardziej zindywidualizowane zachowanie programu w języku.

Istnieją dwa sposoby szerokie, które mogą wchodzić w interakcje XAML i LINQ to XML:

- Ponieważ pliki XAML są poprawnie sformułowany kod XML, można je można tworzyć zapytania i modyfikować za pomocą technologii XML, takich jak LINQ to XML.

- Ponieważ LINQ to XML zapytania stanowią źródło danych, te zapytania może służyć jako źródło danych dla powiązania danych dla elementów interfejsu użytkownika WPF.

W tej dokumentacji opisano drugi scenariusz.

## <a name="data-binding-in-the-windows-presentation-foundation"></a>Powiązywanie danych w Windows Presentation Foundation

Powiązanie danych WPF umożliwia elementu interfejsu użytkownika do jednej z jego właściwości skojarzenia ze źródłem danych. Jest to prosty przykład <xref:System.Windows.Controls.Label> którego tekst przedstawia wartość publiczny właściwości w obiekcie użytkownika. Powiązanie danych WPF opiera się na następujących składników:

|Składnik|Opis|
|---------------|-----------------|
|Wiązanie docelowe|Element interfejsu użytkownika, który ma zostać skojarzony ze źródłem danych. Elementy wizualne na platformie WPF są uzyskiwane z <xref:System.Windows.UIElement> klasy.|
|Właściwość docelowa|*Właściwość zależności* docelowego powiązania, który odzwierciedla wartość źródła powiązanie danych. Właściwości zależności są bezpośrednio obsługiwane przez <xref:System.Windows.DependencyObject> klasy, która <xref:System.Windows.UIElement> pochodzi od klasy.|
|Źródło wiążące|Obiekt źródłowy dla co najmniej jednej wartości, które są dostarczane do elementu interfejsu użytkownika, aby obejrzeć prezentację. WPF automatycznie obsługuje następujące typy jako wiązanie źródeł: CLR obiekty, obiekty danych ADO.NET, dane XML (z lub składnika LINQ to XML kwerendy XPath) lub innego <xref:System.Windows.DependencyObject>.|
|Ścieżka źródłowa|Właściwość źródło powiązania, który jest rozpoznawany jako wartość lub zbiór wartości, która ma zostać powiązany.|

Właściwość zależności jest pojęciem specyficzne dla WPF, który reprezentuje dynamicznie obliczaną właściwością elementu interfejsu użytkownika. Na przykład właściwości zależności często mają wartości domyślne lub wartości, które są dostarczane przez element nadrzędny. Specjalne właściwości są wspierane przez wystąpienia <xref:System.Windows.DependencyProperty> klasy (i nie pola jako standardowe właściwości). Aby uzyskać więcej informacji, zobacz [Przegląd właściwości zależności](/dotnet/framework/wpf/advanced/dependency-properties-overview).

### <a name="dynamic-data-binding-in-wpf"></a>Powiązanie danych dynamicznych w WPF

Domyślnie powiązanie danych występuje tylko wtedy, gdy element interfejsu użytkownika docelowej jest inicjowany. Jest to nazywane *jednorazowe* powiązania. W większości przypadków jest to niewystarczające; zwykle rozwiązaniem powiązanie danych wymaga dynamicznie propagowane zmiany w czasie wykonywania przy użyciu jednej z następujących czynności:

- *Jednokierunkowa* powiązania powoduje, że zmiany po jednej stronie można automatycznie propagowane. Najczęściej zmiany do źródła są uwzględniane w elemencie docelowym, ale odwrotnie Czasami przydatne mogą być.

- W *dwukierunkowe* powiązania, zmiany w źródle są automatycznie propagowane do obiektu docelowego, a zmiany do obiektu docelowego są automatycznie propagowane do źródła.

- Lub dwukierunkowo powiązań, wystąpią, źródło musisz zaimplementować mechanizm powiadamiania zmiany na przykład poprzez implementację <xref:System.ComponentModel.INotifyPropertyChanged> interfejs lub przy użyciu *PropertyNameChanged* wzorca dla każdej właściwości obsługiwane.

Aby uzyskać więcej informacji o wiązaniu danych na platformie WPF, zobacz [powiązanie danych (WPF)](/dotnet/framework/wpf/data/data-binding-wpf).

## <a name="dynamic-properties-in-linq-to-xml-classes"></a>Właściwości dynamiczne w składniku LINQ to XML klasy

Większość klasy programu LINQ to XML nie kwalifikują się jako prawidłowego źródła danych dynamicznych WPF. Niektóre z najbardziej przydatnych informacji jest dostępna wyłącznie za pośrednictwem metody, a nie właściwości i właściwości w ramach tych zajęć, nie należy implementować powiadomienia o zmianach. Aby zapewnić obsługę powiązanie danych WPF, LINQ to XML udostępnia zestaw *właściwości dynamicznych*.

Właściwości dynamiczne są specjalne właściwości czasu wykonywania, które duplikują funkcjonalność istniejących metod i właściwości w <xref:System.Xml.Linq.XAttribute> i <xref:System.Xml.Linq.XElement> klasy. Zostały one dodane do tych klas wyłącznie w celu umożliwienia im na działanie jako źródła danych dynamicznych dla WPF. Aby spełnić te wymagania, te właściwości dynamicznych zaimplementować powiadomienia o zmianach. Szczegółową dokumentację dla tych właściwości dynamicznych znajduje się w następnej sekcji [XML właściwości dynamiczne LINQ to](../designers/linq-to-xml-dynamic-properties.md).

> [!NOTE]
> Znaleziono wiele standardowych właściwości publicznej, w różnych klas w <xref:System.Xml.Linq> przestrzeni nazw może służyć do wiązania danych jednorazowego. Należy jednak pamiętać, że źródłowego ani docelowego nie zostaną dynamicznie zaktualizowane zgodnie z tym systemem.

### <a name="accessing-dynamic-properties"></a>Uzyskiwanie dostępu do właściwości dynamicznej

Właściwości dynamiczne w <xref:System.Xml.Linq.XAttribute> i <xref:System.Xml.Linq.XElement> klasy nie można uzyskać dostępu, takich jak standardowe właściwości. Na przykład w CLR zgodne języków, takich jak C#, mogą nie może być:

- Dostępne bezpośrednio w czasie kompilacji. Właściwości dynamiczne są niewidoczne, aby kompilator i funkcji IntelliSense Visual Studio.

- Odnalezione lub używanych w czasie wykonywania za pomocą odbicia .NET. Nawet w czasie wykonywania nie są one właściwości w tym sensie, podstawowego środowiska CLR.

W języku C#, właściwości dynamicznych są dostępne tylko w czasie wykonywania za pomocą przez <xref:System.ComponentModel> przestrzeni nazw.

Z kolei jednak w formacie XML źródła właściwości dynamicznych jest możliwy za pośrednictwem prostego notacji w następującej postaci:

```xml
<object>.<dynamic-property>
```

Właściwości dynamiczne dla tych dwóch klas rozwiązać jedną wartość, która może być używany bezpośrednio lub działanie indeksatora, który należy podać przy użyciu indeksu w celu uzyskania wynikową wartość lub zbiór wartości. Ostatnie składni ma postać:

```xml
<object>.<dynamic-property>[<index-value>]
```

Aby uzyskać więcej informacji, zobacz [XML właściwości dynamiczne LINQ to](../designers/linq-to-xml-dynamic-properties.md).

Aby zaimplementować wiązanie dynamiczne WPF, właściwości dynamicznych będą używane z przez <xref:System.Windows.Data> przestrzeni nazw, głównie <xref:System.Windows.Data.Binding> klasy.

## <a name="see-also"></a>Zobacz także

- [Powiązanie danych WPF za pomocą LINQ to XML](../designers/wpf-data-binding-with-linq-to-xml-overview.md)
- [Właściwości dynamiczne LINQ to XML](../designers/linq-to-xml-dynamic-properties.md)
- [XAML w WPF](/dotnet/framework/wpf/advanced/xaml-in-wpf)
- [Powiązanie danych (WPF)](/dotnet/framework/wpf/data/data-binding-wpf)
- [Za pomocą znaczników przepływu pracy](http://go.microsoft.com/fwlink/?LinkId=98685)
