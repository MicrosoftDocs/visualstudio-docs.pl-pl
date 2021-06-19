---
title: Zalecenia dotyczące pisania szablonów tekstowych T4
description: Zapoznaj się z ogólnymi wytycznymi, które są przydatne w przypadku generowania kodu programu lub innych zasobów aplikacji w Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4f043e95ef477558028e634bf6b48aded2960ec2
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112386660"
---
# <a name="guidelines-for-writing-t4-text-templates"></a>Zalecenia dotyczące pisania szablonów tekstowych T4

Te ogólne wskazówki mogą być przydatne w przypadku generowania kodu programu lub innych zasobów aplikacji w Visual Studio. Nie są to stałe reguły.

## <a name="guidelines-for-design-time-t4-templates"></a>Wytyczne dotyczące szablonów Design-Time T4

Szablony T4 czasu projektowania to szablony, które generują kod w Visual Studio projektu w czasie projektowania. Aby uzyskać więcej informacji, zobacz Design-Time Code Generation by using T4 Text Templates (Generowanie kodu [w czasie projektowania przy użyciu szablonów tekstowych T4).](../modeling/design-time-code-generation-by-using-t4-text-templates.md)

Generowanie zmiennych aspektów aplikacji.

Generowanie kodu jest najbardziej przydatne w przypadku tych aspektów aplikacji, które mogą ulec zmianie podczas projektu lub mogą ulec zmianie między różnymi wersjami aplikacji. Oddziel te aspekty zmiennych od bardziej niezmiennych aspektów, aby łatwiej określić, co ma zostać wygenerowane. Jeśli na przykład aplikacja udostępnia witrynę internetową, należy oddzielić standardowe funkcje obsługujące strony od logiki definiującej ścieżki nawigacji między stronami.

Kodowanie aspektów zmiennej w co najmniej jednym modelu źródłowym.

Model to plik lub baza danych odczytywana przez każdy szablon w celu uzyskania określonych wartości dla zmiennych części kodu, które mają zostać wygenerowane. Modele mogą być bazami danych, plikami XML o własnym projekcie, diagramami lub językami specyficznym dla domeny. Zazwyczaj jeden model jest używany do generowania wielu plików w Visual Studio projektu. Każdy plik jest generowany na podstawie oddzielnego szablonu.

W projekcie można użyć więcej niż jednego modelu. Można na przykład zdefiniować model nawigacji między stronami internetowymi oraz oddzielny model układu stron.

Skoncentruj model na potrzebach i słownictwie użytkowników, a nie na implementacji.

Na przykład w aplikacji witryny internetowej można oczekiwać, że model będzie odwoływać się do stron internetowych i hiperlinków.

Najlepiej wybrać formę prezentacji, która odpowiada rodzajowi informacji, które reprezentuje model. Na przykład model ścieżek nawigacji za pośrednictwem witryny internetowej może być diagramem pól i strzałek.

Przetestuj wygenerowany kod.

Użyj testów ręcznych lub automatycznych, aby sprawdzić, czy wynikowy kod działa zgodnie z wymaganą przez użytkowników. Unikaj generowania testów z tego samego modelu, z którego jest generowany kod.

W niektórych przypadkach testy ogólne mogą być wykonywane bezpośrednio na modelu. Możesz na przykład napisać test, który gwarantuje, że każda strona w witrynie internetowej będzie osiągana przez nawigację z dowolnej innej strony.

Zezwalaj na kod niestandardowy: generowanie klas częściowych.

Zezwalaj na kod pisany ręcznie oprócz wygenerowanego kodu. Schemat generowania kodu jest nietypowy, ponieważ może uwzględniać wszystkie możliwe odmiany, które mogą wystąpić. W związku z tym należy oczekiwać dodania lub zastąpienia niektórych wygenerowanego kodu. Gdy wygenerowany materiał jest w języku .NET, takim jak C# lub Visual Basic, szczególnie przydatne są dwie strategie:

- Wygenerowane klasy powinny być częściowe. Dzięki temu można dodać zawartość do wygenerowanego kodu.

- Klasy powinny być generowane w parach, a jedna dziedziczy po drugiej. Klasa bazowa powinna zawierać wszystkie wygenerowane metody i właściwości, a klasa pochodna powinna zawierać tylko konstruktory. Dzięki temu kod napisany ręcznie może zastąpić dowolną z wygenerowanych metod.

W innych wygenerowanych językach, takich jak XML, użyj dyrektywy , aby tworzyć proste kombinacje zawartości napisanej ręcznie `<#@include#>` i wygenerowanej. W bardziej złożonych przypadkach może być konieczne napisanie kroku przetwarzania post, który łączy wygenerowany plik z dowolnymi plikami napisanymi ręcznie.

Przenieś wspólny materiał do plików dołączanych lub szablonów czasu działania.

Aby uniknąć powtarzania podobnych bloków tekstu i kodu w wielu szablonach, użyj `<#@ include #>` dyrektywy . Aby uzyskać więcej informacji, zobacz [dyrektywa T4 Include .](../modeling/t4-include-directive.md)

Szablony tekstowe czasu uruchamiania można również tworzyć w oddzielnym projekcie, a następnie wywołać je z szablonu czasu projektowania. W tym celu użyj dyrektywy `<#@ assembly #>` , aby uzyskać dostęp do oddzielnego projektu.

Rozważ przeniesienie dużych bloków kodu do oddzielnego zestawu.

Jeśli masz duże bloki kodu i bloki cech klas, przydatne może być przeniesienie niektórych z tych kodów do metod kompilowanych w oddzielnym projekcie. Możesz użyć dyrektywy `<#@ assembly #>` , aby uzyskać dostęp do kodu w szablonie. Aby uzyskać więcej informacji, zobacz [dyrektywa T4 Assembly .](../modeling/t4-assembly-directive.md)

Metody można umieścić w klasie abstrakcyjnej, która może dziedziczyć szablon. Klasa abstrakcyjna musi dziedziczyć z <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation?displayProperty=fullName> klasy . Aby uzyskać więcej informacji, zobacz [dyrektywa T4 template directive](../modeling/t4-template-directive.md).

Generuj kod, a nie pliki konfiguracji.

Jedną z metod pisania aplikacji zmiennej jest napisanie ogólnego kodu programu, który akceptuje plik konfiguracji. Aplikacja napisana w ten sposób jest bardzo elastyczna i można ją ponownie skonfigurować po zmianie wymagań biznesowych bez konieczności ponownego kompilowania aplikacji. Wadą tego podejścia jest jednak to, że aplikacja będzie działać mniej dobrze niż bardziej konkretną aplikację. Ponadto jego kod programu będzie trudniejszy do odczytania i utrzymania, częściowo dlatego, że zawsze ma do czynienia z najbardziej ogólnymi typami.

Z kolei aplikacja, której części zmiennych są generowane przed kompilacją, może być silnie typowana. Dzięki temu pisanie ręcznie napisanego kodu i integrowanie go z wygenerowanym fragmentem oprogramowania jest znacznie łatwiejsze i bardziej niezawodne.

Aby uzyskać pełną korzyść z generowania kodu, spróbuj wygenerować kod programu zamiast plików konfiguracji.

Użyj folderu Wygenerowany kod.

Umieść szablony i wygenerowane pliki w folderze projektu o nazwie **Generated Code**, aby było jasne, że nie są to pliki, które powinny być edytowane bezpośrednio. Jeśli tworzysz kod niestandardowy w celu zastąpienia lub dodania do wygenerowanych klas, umieść te klasy w folderze o nazwie **Custom Code**. Struktura typowego projektu wygląda następująco:

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

## <a name="guidelines-for-run-time-preprocessed-t4-templates"></a>Wytyczne dotyczące Run-Time (wstępnie przetworzonych) szablonów T4

Przenieś wspólny materiał do dziedziczonych szablonów.

Dziedziczenie umożliwia udostępnianie metod i bloków tekstowych między szablonami tekstowym T4. Aby uzyskać więcej informacji, zobacz [dyrektywa T4 template directive](../modeling/t4-template-directive.md).

Można również użyć plików dołączanych, które mają szablony czasu uruchamiania.

Przenoszenie dużych fragmentów kodu do klasy częściowej.

Każdy szablon czasu uruchamiania generuje definicję klasy częściowej o takiej samej nazwie jak szablon. Można napisać plik kodu, który zawiera inną częściową definicję tej samej klasy. Metody, pola i konstruktory można dodawać do klasy w ten sposób. Te elementy członkowskie mogą być wywoływane z bloków kodu w szablonie.

Zaletą tego działania jest to, że kod jest łatwiejszy do napisania, ponieważ funkcja IntelliSense jest dostępna. Ponadto można osiągnąć lepsze rozdzielenie prezentacji od podstawowej logiki.

Na przykład w **MyReportText.tt**:

`The total is: <#= ComputeTotal() #>`

W **myReportText-Methods.cs:**

`private string ComputeTotal() { ... }`

Zezwalaj na kod niestandardowy: podaj punkty rozszerzenia.

Rozważ wygenerowanie metod wirtualnych w programie \<#+ class feature blocks #> . Dzięki temu pojedynczy szablon może być używany w wielu kontekstach bez żadnych modyfikacji. Zamiast modyfikować szablon, można skonstruować klasę pochodną, która dostarcza minimalną dodatkową logikę. Klasa pochodna może być zwykłym kodem lub szablonem czasu uruchamiania.

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

## <a name="guidelines-for-all-t4-templates"></a>Wytyczne dotyczące wszystkich szablonów T4

Oddzielanie zbierania danych od generowania tekstu.

Staraj się unikać łączenia bloków obliczeniowych i tekstowych. W każdym szablonie tekstowym użyj pierwszego szablonu, \<# code block #> aby ustawić zmienne i wykonać złożone obliczenia. Od pierwszego bloku tekstu aż do końca szablonu lub pierwszego , unikaj długich wyrażeń oraz unikaj pętli i instrukcji warunkowych, chyba że \<#+ class feature block #> zawierają bloki tekstowe. Takie rozwiązanie ułatwia odczytywanie i konserwowanie szablonu.

Nie należy używać `.tt` w przypadku plików dołączanych.

Użyj innego rozszerzenia nazwy pliku, na przykład `.ttinclude` dla plików dołączanych. Należy używać tylko plików, które mają być przetwarzane jako szablony tekstowe w czasie rzeczywistym `.tt` lub w czasie projektowania. W niektórych przypadkach program Visual Studio pliki `.tt` i automatycznie ustawia ich właściwości do przetwarzania.

Każdy szablon należy uruchomić jako stały prototyp.

Napisz przykładowy kod lub tekst, który chcesz wygenerować, i upewnij się, że jest poprawny. Następnie zmień jego rozszerzenie na .tt i stopniowo wstawiaj kod modyfikujący zawartość przez odczytanie modelu.

Rozważ użycie modeli wpisanych.

Mimo że można utworzyć schemat XML lub bazy danych dla modeli, może być przydatne do tworzenia języka specyficznego dla domeny (DSL). DSL ma tę zaletę, że generuje klasę do reprezentowania każdego węzła w schemacie i właściwości do reprezentowania atrybutów. Oznacza to, że można programować w odniesieniu do modelu biznesowego. Na przykład:

```
Team Members:
<# foreach (Person p in team.Members)
 { #>
    <#= p.Name #>
<# } #>
```

Rozważ użycie diagramów dla modeli.

Wiele modeli jest najskuteczniej prezentowanych i zarządzanych po prostu jako tabele tekstowe, zwłaszcza jeśli są bardzo duże.

Jednak w przypadku niektórych rodzajów wymagań biznesowych ważne jest wyjaśnienie złożonych zestawów relacji i przepływów pracy, a diagramy są najbardziej odpowiednie dla średnich. Zaletą diagramu jest łatwa do omówienia z użytkownikami i innymi uczestnikami projektu. Wygenerowanie kodu z modelu na poziomie wymagań biznesowych sprawi, że kod będzie bardziej elastyczny po zmianie wymagań.

Możesz również zaprojektować własny typ diagramu jako język specyficzny dla domeny (DSL). Kod można wygenerować zarówno na podstawie kodu UML, jak i dsls. Aby uzyskać więcej informacji, zobacz [Analyzing and Modeling Architecture (Analizowanie i modelowanie architektury).](../modeling/analyze-and-model-your-architecture.md)

## <a name="see-also"></a>Zobacz też

- [Generowanie kodu czasu projektowania przy użyciu szablonów tekstowych T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md)
- [Generowanie tekstu czasu wykonywania przy użyciu szablonów tekstowych T4](../modeling/run-time-text-generation-with-t4-text-templates.md)
