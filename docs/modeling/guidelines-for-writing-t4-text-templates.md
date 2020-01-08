---
title: Zalecenia dotyczące pisania szablonów tekstowych T4
ms.date: 11/04/2016
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 24c8afd5e34d4957dac3d9f4d5b0e4409ad20895
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75596544"
---
# <a name="guidelines-for-writing-t4-text-templates"></a>Zalecenia dotyczące pisania szablonów tekstowych T4

Te ogólne wskazówki mogą być przydatne w przypadku generowania kodu programu lub innych zasobów aplikacji w programie Visual Studio. Nie są to reguły ustalone.

## <a name="guidelines-for-design-time-t4-templates"></a>Wskazówki dotyczące szablonów T4 czasu projektowania

Szablony T4 w czasie projektowania to szablony generujące kod w projekcie programu Visual Studio w czasie projektowania. Aby uzyskać więcej informacji, zobacz [generowanie kodu w czasie projektowania przy użyciu szablonów tekstowych T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md).

Generuj zmienne aspekty aplikacji.

Generowanie kodu jest najbardziej przydatne w przypadku tych aspektów aplikacji, które mogą ulec zmianie w projekcie, lub zmienią się między różnymi wersjami aplikacji. Należy oddzielić te zmienne aspekty od bardziej niezmiennych aspektów, dzięki czemu można łatwiej określić, co ma zostać wygenerowane. Na przykład jeśli aplikacja udostępnia witrynę sieci Web, należy oddzielić stronę standardową, która obsługuje funkcje z logiki, która definiuje ścieżki nawigacji między stronami.

Koduj zmienne aspekty w jednym lub większej liczbie modeli źródłowych.

Model jest plikiem lub bazą danych, którą każdy szablon odczytuje w celu uzyskania określonych wartości dla zmiennych części kodu, który ma zostać wygenerowany. Modele mogą być bazami danych, plikami XML własnych projektów, diagramów lub języków specyficznych dla domeny. Zazwyczaj jeden model jest używany do generowania wielu plików w projekcie programu Visual Studio. Każdy plik jest generowany na podstawie oddzielnego szablonu.

Można użyć więcej niż jednego modelu w projekcie. Można na przykład zdefiniować model nawigacji między stronami sieci Web a oddzielnym modelem układu stron.

Należy skoncentrować się na modelu w potrzebach i słownictwu użytkowników, a nie w implementacji.

Na przykład w aplikacji witryny sieci Web oczekuje się, że model odwołuje się do stron sieci Web i hiperłączy.

Najlepiej, aby wybrać formę prezentacji, która odpowiada typowi informacji reprezentowanej przez ten model. Na przykład model ścieżek nawigacyjnych za pomocą witryny sieci Web może być diagramem pól i strzałek.

Przetestuj wygenerowany kod.

Użyj ręcznych lub zautomatyzowanych testów, aby sprawdzić, czy otrzymany kod działa zgodnie z potrzebami użytkowników. Unikaj generowania testów z tego samego modelu, z którego jest generowany kod.

W niektórych przypadkach ogólne testy mogą być wykonywane bezpośrednio na modelu. Można na przykład napisać test, który zapewnia, że każda Strona w witrynie sieci Web może zostać osiągnięta przez nawigację z innych.

Zezwalaj na kod niestandardowy: Generuj klasy częściowe.

Zezwalaj na kod, który można napisać ręcznie, oprócz wygenerowanego kodu. Schemat generowania kodu jest nietypowy, aby można było uwzględnić wszystkie możliwe zmiany, które mogą wystąpić. W związku z tym należy oczekiwać, aby dodać lub zastąpić część wygenerowanego kodu. W przypadku, gdy wygenerowany materiał znajduje się w języku .NET C# , takim jak lub Visual Basic, są szczególnie przydatne dwie strategie:

- Wygenerowane klasy powinny być częściowe. Pozwala to na dodawanie zawartości do wygenerowanego kodu.

- Klasy powinny być generowane w parach, po jednym dziedziczeniu. Klasa bazowa powinna zawierać wszystkie wygenerowane metody i właściwości, a Klasa pochodna powinna zawierać tylko konstruktory. Pozwala to na ręczne pisanie kodu w celu przesłonięcia dowolnej z wygenerowanych metod.

W innych wygenerowanych językach, takich jak XML, użyj dyrektywy `<#@include#>`, aby tworzyć proste kombinacje zawartości z ręcznym i wygenerowanym. W bardziej złożonych przypadkach może być konieczne napisanie kroku przetwarzania końcowego, który łączy wygenerowany plik z dowolnymi plikami ręcznymi.

Przenieś wspólny materiał do plików dołączanych lub szablonów czasu wykonywania.

Aby uniknąć powtarzania podobnych bloków tekstu i kodu w wielu szablonach, użyj dyrektywy `<#@ include #>`. Aby uzyskać więcej informacji, zobacz [T4 include dyrektywy](../modeling/t4-include-directive.md).

Możesz również utworzyć szablony tekstu w czasie wykonywania w osobnym projekcie, a następnie wywołać je z szablonu czasu projektowania. Aby to zrobić, użyj dyrektywy `<#@ assembly #>` w celu uzyskania dostępu do oddzielnego projektu.

Rozważ przeniesienie dużych bloków kodu do oddzielnego zestawu.

Jeśli masz duże bloki kodu i bloki funkcji klasy, warto przenieść część tego kodu do metod kompilowanych w osobnym projekcie. Aby uzyskać dostęp do kodu w szablonie, można użyć dyrektywy `<#@ assembly #>`. Aby uzyskać więcej informacji, zobacz [Dyrektywa zestawu T4](../modeling/t4-assembly-directive.md).

Metody można umieścić w klasie abstrakcyjnej, którą szablon może dziedziczyć. Klasa abstrakcyjna musi dziedziczyć po <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation?displayProperty=fullName>. Aby uzyskać więcej informacji, zobacz [dyrektywa dotycząca szablonu T4](../modeling/t4-template-directive.md).

Generuj kod, a nie pliki konfiguracji.

Jedną z metod pisania zmiennej aplikacji jest zapisanie kodu programu generycznego, który akceptuje plik konfiguracji. Aplikacja zapisywana w ten sposób jest bardzo elastyczna i można ją ponownie skonfigurować w przypadku zmiany wymagań firmy, bez konieczności ponownego kompilowania aplikacji. Jednak Wadą tego podejścia jest to, że aplikacja będzie działać mniej dobrze niż bardziej konkretna aplikacja. Ponadto kod programu będzie trudniejszy do odczytania i utrzymania, częściej, ponieważ zawsze zajmuje się najbardziej ogólnymi typami.

Z drugiej strony, której części zmiennych są generowane, zanim kompilacja może być silnie wpisana. Dzięki temu można znacznie łatwiej i bardziej niezawodny pisać kod napisany ręcznie i zintegrować go z wygenerowanymi częściami oprogramowania.

Aby uzyskać pełne korzyści wynikające z generowania kodu, spróbuj wygenerować kod programu zamiast plików konfiguracji.

Użyj wygenerowanego folderu kodu.

Umieść szablony i wygenerowane pliki w folderze projektu o nazwie **wygenerowany kod**, aby wyjaśnić, że nie są to pliki, które powinny być edytowane bezpośrednio. W przypadku tworzenia niestandardowego kodu do przesłonięcia lub dodania do wygenerowanych klas należy umieścić te klasy w folderze o nazwie **kod niestandardowy**. Struktura typowego projektu wygląda następująco:

```
MyProject
   Custom Code
      Class1.cs
      Class2.cs
   Generated Code
      Class1.tt
          Class1.cs
      Class2.tt
          Class2.cs
   AnotherClass.cs
```

## <a name="guidelines-for-run-time-preprocessed-t4-templates"></a>Wytyczne dotyczące czasu wykonywania (wstępnie przetworzonych) szablonów T4

Przenieś wspólny materiał do dziedziczonych szablonów.

Dziedziczenie umożliwia udostępnianie metod i bloków tekstu między szablonami tekstu T4. Aby uzyskać więcej informacji, zobacz [dyrektywa dotycząca szablonu T4](../modeling/t4-template-directive.md).

Można również użyć plików dołączanych, które mają Szablony czasu wykonywania.

Przenieś duże treści kodu do klasy częściowej.

Każdy szablon czasu wykonywania generuje definicję klasy częściowej, która ma taką samą nazwę jak szablon. Można napisać plik kodu, który zawiera inną definicję częściową tej samej klasy. W ten sposób można dodać metody, pola i konstruktory do klasy. Te elementy członkowskie mogą być wywoływane z bloków kodu w szablonie.

Zaletą tej metody jest łatwiejsze pisanie kodu, ponieważ technologia IntelliSense jest dostępna. Ponadto można uzyskać lepszy rozdzielenie między prezentacją a podstawową logiką.

Na przykład w **MyReportText.tt**:

`The total is: <#= ComputeTotal() #>`

W **MyReportText-Methods.cs**:

`private string ComputeTotal() { ... }`

Zezwalaj na kod niestandardowy: Podaj punkty rozszerzenia.

Należy rozważyć generowanie metod wirtualnych w \<# + bloki funkcji klasy # >. Pozwala to na użycie jednego szablonu w wielu kontekstach bez modyfikacji. Zamiast modyfikować szablon, można utworzyć klasę pochodną, która dostarcza minimalną dodatkową logikę. Klasa pochodna może być zwykłym kodem lub szablonem czasu wykonywania.

Na przykład w MyStandardRunTimeTemplate.tt:

```
This page is copyright <#= CompanyName() #>.
<#+ protected virtual string CompanyName() { return ""; } #>
```

W kodzie aplikacji:

```
class FabrikamTemplate : MyStandardRunTimeTemplate
{
  protected override string CompanyName() { return "Fabrikam"; }
}
...
  string PageToDisplay = new FabrikamTemplate().TextTransform();
```

## <a name="guidelines-for-all-t4-templates"></a>Wskazówki dotyczące wszystkich szablonów T4

Oddzielne zbieranie danych z generacji tekstu.

Staraj się unikać mieszania obliczeń i bloków tekstowych. W każdym szablonie tekstu użyj pierwszej \<# # Code # >, aby ustawić zmienne i wykonywać złożone obliczenia. Od pierwszego bloku tekstu do końca szablonu lub pierwszej \<# + blok funkcji klasy # >, unikania długich wyrażeń i unikania pętli i warunkowych, chyba że zawierają bloki tekstu. To rozwiązanie ułatwia odczytywanie i konserwowanie szablonu.

Nie używaj `.tt` w przypadku plików dołączanych.

Użyj innego rozszerzenia nazwy pliku, takiego jak `.ttinclude` dla plików dołączanych. Używaj `.tt` tylko dla plików, które mają być przetwarzane jako szablony tekstu w czasie wykonywania lub w czasie projektowania. W niektórych przypadkach program Visual Studio rozpoznaje pliki `.tt` i automatycznie ustawia ich właściwości do przetwarzania.

Uruchom każdy szablon jako stały prototyp.

Napisz przykład kodu lub tekstu, który ma zostać wygenerowany, i upewnij się, że jest on poprawny. Następnie zmień jego rozszerzenie na. tt i przyrostowo Wstaw kod, który modyfikuje zawartość, odczytując model.

Należy rozważyć użycie modeli z typem.

Chociaż dla modeli można utworzyć schemat XML lub bazę danych, może być przydatne utworzenie języka specyficznego dla domeny (DSL). DSL ma zalety generowania klasy do reprezentowania każdego węzła w schemacie oraz właściwości do reprezentowania atrybutów. Oznacza to, że można programować zgodnie z modelem biznesowym. Na przykład:

```
Team Members:
<# foreach (Person p in team.Members)
 { #>
    <#= p.Name #>
<# } #>
```

Rozważ użycie diagramów dla modeli.

Wiele modeli jest najbardziej efektywnie prezentowanych i zarządzanych po prostu jako tabele tekstowe, zwłaszcza jeśli są bardzo duże.

Jednakże w przypadku niektórych rodzajów wymagań firmy ważne jest, aby wyjaśnić złożone zestawy relacji i przepływy pracy, a diagramy są najlepszym odpowiednim nośnikiem. Zaletą diagramu jest łatwość dyskusji z użytkownikami i innymi uczestnikami projektu. Generując kod z modelu na poziomie wymagań firmy, można zwiększyć elastyczność kodu w przypadku zmiany wymagań.

Możesz również projektować własny typ diagramu jako język specyficzny dla domeny (DSL). Kod można generować z poziomu języka UML i językami DSL. Aby uzyskać więcej informacji, zobacz [analizowanie i modelowanie architektury](../modeling/analyze-and-model-your-architecture.md).

## <a name="see-also"></a>Zobacz także

- [Generowanie kodu czasu projektowania przy użyciu szablonów tekstowych T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md)
- [Generowanie tekstu czasu wykonywania przy użyciu szablonów tekstowych T4](../modeling/run-time-text-generation-with-t4-text-templates.md)
