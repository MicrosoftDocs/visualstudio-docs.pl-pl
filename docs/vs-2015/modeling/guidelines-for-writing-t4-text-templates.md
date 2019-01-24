---
title: Zalecenia dotyczące pisania szablonów tekstowych T4 | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 04dd3fc4-10e8-488a-bdea-4d615f50f063
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 542b43b5addad1bee59921bd2f4b593ea4676c59
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54795355"
---
# <a name="guidelines-for-writing-t4-text-templates"></a>Zalecenia dotyczące pisania szablonów tekstowych T4
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Te ogólne wytyczne mogą być przydatne w przypadku generowania kodu programu lub innych zasobów aplikacji w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Zasady nie zostały ustalone.  
  
## <a name="guidelines-for-design-time-t4-templates"></a>Wytyczne dotyczące szablonów T4 w czasie projektowania  
 Szablony T4 czasu projektowania są szablony, które generują kod w swojej [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] projektu w czasie projektowania. Aby uzyskać więcej informacji, zobacz [generowanie kodu czasu projektowania przy użyciu szablonów tekstowych T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md).  
  
 Generuj zmienną aspektów aplikacji.  
 Generowanie kodu jest najbardziej użyteczne dla tych aspektów aplikacji, które mogą ulec zmianie w trakcie realizacji projektu lub zmieni się między różnymi wersjami aplikacji. Oddzielne te aspekty zmiennej z aspektów bardziej niezmiennej, tak, aby łatwiej określić, co ma zostać wygenerowane. Na przykład jeśli aplikacja zawiera witrynę sieci Web, należy oddzielić standardowej strony obsługująca funkcje z logikę, która definiuje ścieżki nawigacji z jednej strony do innego.  
  
 Kodowanie zmiennej aspekty w co najmniej jednego modelu źródłowego.  
 Model jest pliku lub bazy danych, która odczytuje każdy szablon, można uzyskać określone wartości dla zmiennej części kodu, który ma zostać wygenerowane. Modele mogą być baz danych i plików XML, własny projekt, diagramy lub języków specyficznych dla domeny. Zazwyczaj jeden model jest używany do generowania wielu plików w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] projektu. Każdy plik jest generowany na podstawie szablonu oddzielne.  
  
 Można użyć więcej niż jednego modelu w projekcie. Na przykład można zdefiniować model nawigacji między stronami sieci Web i osobnymi plikami modelu dla układu strony.  
  
 Na potrzeby użytkowników i słownictwa, a nie na implementacji, należy skoncentrować się modelu.  
 Na przykład w aplikacji witryny sieci Web, można oczekiwać modelu do odwoływania się do strony sieci Web i hiperłączy.  
  
 W idealnym przypadku Wybierz formę prezentacji, która odpowiada rodzaju informacje, który reprezentuje model. Na przykład model nawigacyjnych ścieżek za pośrednictwem witryny sieci Web może być diagram pola i strzałki.  
  
 Przetestuj wygenerowanego kodu.  
 Aby sprawdzić, czy powstały kod działa zgodnie z użytkownicy muszą, należy użyć testy ręczne lub automatyczne. Należy unikać Generowanie testów z tego samego modelu, z którego jest generowany kod.  
  
 W niektórych przypadkach ogólne można wykonać testy na podstawie modelu bezpośrednio. Na przykład można napisać test, który zapewnia, że każdej strony w witrynie sieci Web jest osiągalna nawigacji od innych.  
  
 Zezwalaj na niestandardowego kodu: Generuj klasy częściowe.  
 Zezwalaj na kod, który można zapisać ręcznie dodatkowo do wygenerowanego kodu. Jest nietypowy dla schematu generowania kodu można było uwzględnić wszystkie ewentualne zmiany, które mogą wystąpić. Dlatego należy oczekiwać dodać lub zmienić niektóre z wygenerowanego kodu. Gdzie wygenerowanego materiału jest w języku .NET takich jak [!INCLUDE[csprcs](../includes/csprcs-md.md)] lub [!INCLUDE[vbprvb](../includes/vbprvb-md.md)], są szczególnie przydatne, dwóch strategii:  
  
- Wygenerowane klasy powinna być częściowe. Dzięki temu można dodać zawartości do wygenerowanego kodu.  
  
- Klas powinny być generowane w parach, jeden dziedziczenie w innej. Klasa bazowa powinien zawierać wszystkie wygenerowane metody i właściwości, a klasa pochodna może zawierać tylko konstruktory. Dzięki temu kod odręcznej do żadnego z wygenerowanych metod zastąpienia.  
  
  W innych językach wygenerowane, takich jak XML, należy użyć `<#@include#>` dyrektywy, aby proste kombinacji odręcznej i generowanej zawartości. W bardziej złożonych przypadkach trzeba napisać kroku przetwarzania końcowego, który łączy wygenerowany plik z plikami odręcznej.  
  
  Przenieś wspólnej materiały do dołączonych plików lub szablonów czasu wykonywania  
  Aby uniknąć powtarzania podobne bloków tekstu i kodu w różnych szablonach, użyj `<#@ include #>` dyrektywy. Aby uzyskać więcej informacji, zobacz [dyrektywy zawierają T4](../modeling/t4-include-directive.md).  
  
  Można również tworzyć szablony tekstowe czasu wykonywania w osobnym projekcie, a następnie wywołaj je z szablonu w czasie projektowania. Aby to zrobić, należy użyć `<#@ assembly #>` dyrektywy do dostępu do oddzielnego projektu. Aby uzyskać przykłady, zobacz ["Dziedziczenie w szablonów tekstowych" w blogu Gareth Jones](http://go.microsoft.com/fwlink/?LinkId=208373).  
  
  Należy rozważyć przeniesienie dużych bloków kodu w osobnym zestawie.  
  Jeśli masz kod dużych bloków i bloki cech klas może być przydatne przenieść niektóre ten kod do metody, które kompilujesz w osobnym projekcie. Możesz użyć `<#@ assembly #>` dyrektywy, aby uzyskiwać dostęp do kodu w szablonie. Aby uzyskać więcej informacji, zobacz [dyrektywa T4 dotycząca zestawu](../modeling/t4-assembly-directive.md).  
  
  Metody można umieścić w klasę abstrakcyjną, która może dziedziczyć szablonu. Klasa ogólna musi dziedziczyć <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation?displayProperty=fullName>. Aby uzyskać więcej informacji, zobacz [dyrektywa T4 dotycząca szablonu](../modeling/t4-template-directive.md).  
  
  Generowanie kodu, nie pliki konfiguracji  
  Jedną z metod zapisu zmiennych wniosek jest pisanie kodu ogólny program, który akceptuje pliku konfiguracji. Aplikacji napisanych w ten sposób jest bardzo elastyczny i można tak skonfigurować, po zmianie wymagań biznesowych, bez ponownie skompilować aplikację. Jednak wadą tego podejścia jest będą wykonywane przez aplikację również, mniej niż aplikacja bardziej szczegółowe. Ponadto jego kod programu, będzie trudniejsze do odczytu i utrzymywania częściowo, ponieważ jest ona zawsze ma do czynienia z najbardziej ogólnych typów.  
  
  Z drugiej strony, których części zmiennych są generowane przed kompilacją aplikacji może być silnie typizowane. Dzięki temu znacznie prostszy i bardziej niezawodne pisać kod odręcznej i zintegrować ją z wygenerowanym części oprogramowania.  
  
  Aby uzyskać pełne zaletą generowania kodu, spróbuj do generowania kodu programu zamiast plików konfiguracyjnych.  
  
  Użyj folderu wygenerowany kod  
  Umieść szablony i wygenerowane pliki w folderze projektu o nazwie **wygenerowany kod**, aby go wyczyścić, że nie są pliki, które powinny być edytowany bezpośrednio. Jeśli tworzysz kod niestandardowy, aby zastąpić, lub dodać do wygenerowanych klas, umieszczenie tych klas w folderze o nazwie **kod niestandardowy**. Struktura w typowym projekcie wygląda następująco:  
  
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
  
## <a name="guidelines-for-run-time-preprocessed-t4-templates"></a>Wytyczne dotyczące szablonów T4 (wstępnie przetworzony) czasu wykonywania  
 Przenieś wspólnej materiały do dziedziczonych szablonów  
 Dziedziczenie umożliwia udostępnianie metody i bloki tekstu między szablonów tekstowych T4. Aby uzyskać więcej informacji, zobacz [dyrektywa T4 dotycząca szablonu](../modeling/t4-template-directive.md).  
  
 Można również użyć obejmują pliki, które mają szablonów czasu wykonywania.  
  
 Przenieś dużych treści kodu do klasy częściowej.  
 Każdy szablon czasu wykonywania generuje definicję klasy częściowej, która ma taką samą nazwę jako szablonu. Można napisać plik kodu, który zawiera innej definicji częściowej tej samej klasy. Możesz dodać metody, pola i Konstruktory klasy w ten sposób. Te elementy członkowskie można wywołać z bloków kodu w szablonie.  
  
 Zaletą w ten sposób jest to kod jest łatwiejszy do zapisu, ponieważ IntelliSense jest dostępna. Ponadto można osiągnąć lepszą rozdzielenie prezentacji i podstawowej logiki.  
  
 Na przykład w **MyReportText.tt**:  
  
 `The total is: <#= ComputeTotal() #>`  
  
 W **MyReportText Methods.cs**:  
  
 `private string ComputeTotal() { ... }`  
  
 Zezwalaj na niestandardowego kodu: Podaj punkty rozszerzenia  
 Weź pod uwagę Generowanie metody wirtualne \<#+ klasy funkcja blokuje #>. Umożliwia to pojedynczy szablon ma być używany w wielu kontekstach bez żadnych modyfikacji. Zamiast modyfikowania szablonu, można utworzyć pochodnej klasy, która dostarcza minimalne dodatkowej logiki. Klasa pochodna może być albo regularne kodu lub może być szablon czasu wykonywania.  
  
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
  
## <a name="guidelines-for-all-t4-templates"></a>Wytyczne dotyczące wszystkie szablony T4  
 Oddzielaj zbieranie danych od Generowanie tekstu  
 Staraj się unikać mieszania obliczeń i bloków tekstu. W każdym szablonie tekstu należy użyć pierwszego \<kod # block #> do ustawiania zmiennych i wykonywania złożonych obliczeń. Z pierwszego bloku tekstu w dół do końca szablonu lub pierwszy \<cechę klasy #+ block #> Unikaj długich wyrażeń i uniknąć pętli i warunkowych, chyba że zawierają bloki tekstu. Praktyka ta sprawia, że szablon jest łatwiej odczytywać i obsługa.  
  
 Nie używaj `.tt` dołączonych plików  
 Używanie innym rozszerzeniem nazwy pliku, takiej jak `.ttinclude` dołączonych plików. Użyj `.tt` tylko dla plików, które mają być przetwarzane w czasie wykonywania lub czasu projektowania szablonów tekstowych. W niektórych przypadkach [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] rozpoznaje `.tt` pliki i automatycznie ustawia jego właściwości dla przetwarzania.  
  
 Rozpoczęcie każdego szablonu jako stały prototypu.  
 Napisz przykładem kodu lub tekstu, który chcesz wygenerować i upewnij się, że jest on poprawny. Następnie zmień jego rozszerzenie na .tt po czym stopniowo wstawiać kod, który modyfikuje zawartość, czytając modelu.  
  
 Należy rozważyć użycie wpisane modeli.  
 Mimo że za tworzenie schematu XML lub bazy danych dla modeli, może być przydatne do tworzenia języka specyficznego dla domeny (DSL). DSL ma tę zaletę, generuje klasę do reprezentowania każdego węzła w schemacie i właściwości do reprezentowania atrybutów. Oznacza to, że można programować pod względem modelu biznesowego. Na przykład:  
  
```  
Team Members:  
<# foreach (Person p in team.Members)   
 { #>   
    <#= p.Name #>   
<# } #>  
```  
  
 Należy wziąć pod uwagę dla modeli za pomocą diagramów.  
 Wiele modeli najbardziej efektywny sposób prezentowania i zarządzane po prostu jako tabeli tekstu, zwłaszcza, jeśli są one bardzo duże.  
  
 Jednak dla niektórych rodzajów wymagań biznesowych, jest ważne wyjaśnić, złożonych zestawów relacje i przepływów pracy i diagramy są najlepiej nadaje się nośnika. Zaletą diagram jest jest łatwy w celu omówienia ich z użytkownikami i innych zainteresowanych stron. Przez generowanie kodu z modelem na poziomie wymagań biznesowych, możesz sprawić, że kod większą elastyczność podczas zmiany wymagań.  
  
 Diagramy klas i aktywności UML można dostosować do tych celów. Istnieje również możliwość projektowania swój własny typ diagramu jako języka specyficznego dla domeny (DSL). Kod można wygenerować z UML i języków DSL. Aby uzyskać więcej informacji, zobacz [analizowanie i modelowanie architektury](../modeling/analyze-and-model-your-architecture.md) i [analizowanie i modelowanie architektury](../modeling/analyze-and-model-your-architecture.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Generowanie kodu czasu projektowania przy użyciu szablonów tekstowych T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md)   
 [Generowanie tekstu czasu wykonywania przy użyciu szablonów tekstowych T4](../modeling/run-time-text-generation-with-t4-text-templates.md)
