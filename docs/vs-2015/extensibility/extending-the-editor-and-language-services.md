---
title: Rozszerzanie usług edytora i języka | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new -
ms.assetid: 8d04f8db-eda7-4b3e-b6eb-c06df104502a
caps.latest.revision: 23
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 91eab151680d936c350c8c5745aec6c9fe86e47c
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51723069"
---
# <a name="extending-the-editor-and-language-services"></a>Rozszerzanie usług edytora i językowych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dodawanie funkcji do usługi języka (takie jak IntelliSense) do własnego edytora i rozszerzenia większość funkcji edytora kodu Visual Studio.  Aby uzyskać pełną listę można rozszerzyć, zobacz [usługi językowej i edytora punkty rozszerzenia](../extensibility/language-service-and-editor-extension-points.md).  
  
 Większość funkcji edytora można rozszerzyć za pomocą Managed Extensibility Framework (MEF). Na przykład, jeśli funkcja edytora, aby rozszerzyć kolorowanie składni, należy napisać MEF *część* definiujący klasyfikacje, dla których ma inną kolorowanie i sposobu ich obsługi. Edytor obsługuje również wiele rozszerzeń w tej samej funkcji.  
  
 Warstwa prezentacji edytora bazuje Windows Presentation Framework (WPF). WPF zawiera bibliotekę graficzną elastyczne formatowania tekstu, a także wizualizacji, takich jak grafiki i animacje.  
  
 Visual Studio SDK zawiera kart znanych jako *podkładki* do obsługi pakietów VSPackage, napisanych dla wcześniejszych wersji. Niemniej jednak w przypadku istniejącego pakietu VSPackage, zaleca się zaktualizować go do nowej technologii w celu uzyskania lepszej wydajności i niezawodności.  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Wprowadzenie do rozszerzeń usługi językowej i edytora](../extensibility/getting-started-with-language-service-and-editor-extensions.md)|Wyjaśnia, jak utworzyć rozszerzenie edytora.|  
|[Wewnątrz edytora](../extensibility/inside-the-editor.md)|W tym artykule opisano ogólną strukturę edytora i wyświetla część jej dostępnych funkcji.|  
|[Struktura Managed Extensibility Framework (MEF) w edytorze](../extensibility/managed-extensibility-framework-in-the-editor.md)|Wyjaśnia, jak Managed Extensibility Framework (MEF) za pomocą edytora.|  
|[Punkty rozszerzeń usługi językowej i edytora](../extensibility/language-service-and-editor-extension-points.md)|Wyświetla listę punktów rozszerzenia edytora. Punkty rozszerzenia reprezentują funkcje edytora, które mogą zostać rozszerzone.|  
|[Przewodnik: tworzenie zakończeń, poleceń i ustawień widoku (prowadnice kolumn)](../extensibility/walkthrough-creating-a-view-adornment-commands-and-settings-column-guides.md)|Przeprowadzi i wyjaśniono tworzenie zakończeń widoku, który Rysuje linie gudie kolumn zabezpieczać kodu na szerokość ekranu.  Pokazuje również, odczytywania i zapisywania ustawień, a także deklarowania i wykonania polecenia, które można wywoływać z okna poleceń.|  
|[Importy edytora](../extensibility/editor-imports.md)|Wyświetla listę usług, które można importować rozszerzenia.|  
|[Dostosowanie starszego kodu do edytora](../extensibility/adapting-legacy-code-to-the-editor.md)|W tym artykule wyjaśniono różne sposoby dostosowania starszego kodu (wcześniej Visual Studio 2010) do rozszerzenia edytora.|  
|[Migrowanie starszej wersji usługi językowej](../extensibility/internals/migrating-a-legacy-language-service.md)|Wyjaśnia, jak przeprowadzić migrację usługi językowej na podstawie pakietu VSPackage.|  
|[Przewodnik: łączenie typu zawartości z rozszerzeniem nazwy pliku](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)|Pokazuje, jak połączyć typu zawartości z rozszerzeniem nazwy pliku.|  
|[Przewodnik: tworzenie symbolu na marginesie](../extensibility/walkthrough-creating-a-margin-glyph.md)|Pokazuje, jak dodać ikonę margines.|  
|[Przewodnik: wyróżnianie tekstu](../extensibility/walkthrough-highlighting-text.md)|Ilustruje sposób używania *tagi* aby wyróżnić tekst.|  
|[Przewodnik: tworzenie konspektu](../extensibility/walkthrough-outlining.md)|Pokazuje, jak dodać konspekt dla konkretnych rodzajów nawiasów klamrowych.|  
|[Przewodnik: wyświetlanie parowanych nawiasów klamrowych](../extensibility/walkthrough-displaying-matching-braces.md)|Pokazuje, jak wyróżnianie pasujących nawiasów klamrowych.|  
|[Przewodnik: wyświetlanie etykietek narzędzi SzybkieInfo](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)|Pokazuje sposób wyświetlania okna podręczne skrócone informacje, które opisują elementy kodu, takie jak właściwości, metody i zdarzenia.|  
|[Przewodnik: wyświetlanie pomocy dotyczącej sygnatur](../extensibility/walkthrough-displaying-signature-help.md)|Pokazuje sposób wyświetlania okna podręczne, które zapewniają informacje o liczbę i typy parametrów w podpisie.|  
|[Przewodnik: wyświetlanie uzupełniania instrukcji](../extensibility/walkthrough-displaying-statement-completion.md)|Pokazuje, jak zaimplementować uzupełniania instrukcji.|  
|[Przewodnik: implementowanie fragmentów kodu](../extensibility/walkthrough-implementing-code-snippets.md)|Pokazuje, jak zaimplementować rozszerzenia fragmentu kodu.|  
|[Przewodnik: wyświetlanie sugestii „żarówka”](../extensibility/walkthrough-displaying-light-bulb-suggestions.md)|Pokazuje sposób wyświetlania żarówki dla kodu sugestie.|  
|[Przewodnik: używanie polecenia programu PowerShell z rozszerzeniem edytora](../extensibility/walkthrough-using-a-shell-command-with-an-editor-extension.md)|Pokazuje, jak kojarzenie polecenia menu w VSPackage za pomocą składnika MEF.|  
|[Przewodnik: używanie klawisza skrótu z rozszerzeniem edytora](../extensibility/walkthrough-using-a-shortcut-key-with-an-editor-extension.md)|Pokazuje, jak skojarzyć skrótu w menu w VSPackage z składnik MEF.|  
|[Managed Extensibility Framework (MEF)](http://msdn.microsoft.com/library/6c61b4ec-c6df-4651-80f1-4854f8b14dde)|Zawiera informacje na temat Managed Extensibility Framework (MEF).|  
|[Windows Presentation Foundation](http://msdn.microsoft.com/library/f667bd15-2134-41e9-b4af-5ced6fafab5d)|Zawiera informacje o Windows Presentation Foundation (WPF).|  
  
## <a name="reference"></a>Tematy pomocy  
 Edytor programu Visual Studio zawiera następujące przestrzenie nazw.  
  
 <xref:Microsoft.VisualStudio.Language.Intellisense>  
  
 <xref:Microsoft.VisualStudio.Language.StandardClassification>  
  
 <xref:Microsoft.VisualStudio.Editor>  
  
 <xref:Microsoft.VisualStudio.Text>  
  
 <xref:Microsoft.VisualStudio.Text.Adornments>  
  
 <xref:Microsoft.VisualStudio.Text.Classification>  
  
 <xref:Microsoft.VisualStudio.Text.Differencing>  
  
 <xref:Microsoft.VisualStudio.Text.Document>  
  
 <xref:Microsoft.VisualStudio.Text.Editor>  
  
 <xref:Microsoft.VisualStudio.Text.Editor.OptionsExtensionMethods>  
  
 <xref:Microsoft.VisualStudio.Text.Formatting>  
  
 <xref:Microsoft.VisualStudio.Text.IncrementalSearch>  
  
 <xref:Microsoft.VisualStudio.Text.Operations>  
  
 <xref:Microsoft.VisualStudio.Text.Outlining>  
  
 <xref:Microsoft.VisualStudio.Text.Projection>  
  
 <xref:Microsoft.VisualStudio.Text.Tagging>  
  
 <xref:Microsoft.VisualStudio.Utilities>

