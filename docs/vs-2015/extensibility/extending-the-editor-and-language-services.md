---
title: Rozszerzanie edytora i usług językowych | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new -
ms.assetid: 8d04f8db-eda7-4b3e-b6eb-c06df104502a
caps.latest.revision: 23
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 085e1b5c1fbfbbaf5649966738f2864e0b72ed35
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65674784"
---
# <a name="extending-the-editor-and-language-services"></a>Rozszerzanie usług edytora i językowych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Funkcje usługi językowej (na przykład IntelliSense) można dodać do własnego edytora i rozłożyć większość funkcji edytora kodu programu Visual Studio.  Aby uzyskać pełną listę elementów, które można rozszerzać, zobacz [punkty rozszerzenia usługi językowej i edytora](../extensibility/language-service-and-editor-extension-points.md).  
  
 Większość funkcji edytora można rozłożyć przy użyciu Managed Extensibility Framework (MEF). Na przykład, jeśli funkcja edytora, która ma zostać rozszerzona, ma kolorowanie składni, można napisać *część składnika* MEF, która definiuje klasyfikacje, dla których ma być różne kolorowanie i w jaki sposób mają być obsługiwane. Edytor obsługuje również wiele rozszerzeń tej samej funkcji.  
  
 Warstwa prezentacji edytora jest oparta na strukturze prezentacji systemu Windows (WPF). WPF udostępnia bibliotekę grafiki do elastycznego formatowania tekstu, a także udostępnia wizualizacje, takie jak grafika i animacje.  
  
 Zestaw Visual Studio SDK zawiera karty, które są nazywane *podkładkami* do obsługi pakietów VSPackage utworzonych dla wcześniejszych wersji. Jeśli jednak masz istniejący pakietu VSPackage, Zalecamy zaktualizowanie go do nowej technologii w celu uzyskania lepszej wydajności i niezawodności.  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Wprowadzenie do rozszerzeń usługi językowej i edytora](../extensibility/getting-started-with-language-service-and-editor-extensions.md)|Wyjaśnia, jak utworzyć rozszerzenie dla edytora.|  
|[Wewnątrz edytora](../extensibility/inside-the-editor.md)|Zawiera opis ogólnej struktury edytora i zawiera listę jego funkcji.|  
|[Struktura Managed Extensibility Framework (MEF) w edytorze](../extensibility/managed-extensibility-framework-in-the-editor.md)|Wyjaśnia, jak używać Managed Extensibility Framework (MEF) z edytorem.|  
|[Punkty rozszerzeń usługi językowej i edytora](../extensibility/language-service-and-editor-extension-points.md)|Wyświetla listę punktów rozszerzenia edytora. Punkty rozszerzenia reprezentują funkcje edytora, które można rozszerzyć.|  
|[Przewodnik: tworzenie zakończeń, poleceń i ustawień widoku (prowadnice kolumn)](../extensibility/walkthrough-creating-a-view-adornment-commands-and-settings-column-guides.md)|Instruktaże i objaśniające tworzenie zakończenia tworzenia widoku, który rysuje linie kolumn gudie, aby ułatwić zachowanie kodu do określonej szerokości wyświetlania.  Pokazuje również ustawienia odczytu i zapisu, a także deklarując i implementując polecenia, które można wywołać z okna poleceń.|  
|[Importy edytora](../extensibility/editor-imports.md)|Wyświetla listę usług, które mogą importować rozszerzenia.|  
|[Dostosowanie starszego kodu do edytora](../extensibility/adapting-legacy-code-to-the-editor.md)|Wyjaśnia różne sposoby adaptacji starszego kodu (wersja wstępna programu Visual Studio 2010) w celu rozbudowania edytora.|  
|[Migrowanie starszej wersji usługi językowej](../extensibility/internals/migrating-a-legacy-language-service.md)|Wyjaśnia, w jaki sposób przeprowadzić migrację usługi językowej opartej na pakietu VSPackage.|  
|[Przewodnik: łączenie typu zawartości z rozszerzeniem nazwy pliku](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)|Pokazuje, jak połączyć typ zawartości z rozszerzeniem nazwy pliku.|  
|[Przewodnik: tworzenie symbolu na marginesie](../extensibility/walkthrough-creating-a-margin-glyph.md)|Pokazuje, jak dodać ikonę do marginesu.|  
|[Przewodnik: wyróżnianie tekstu](../extensibility/walkthrough-highlighting-text.md)|Pokazuje, jak używać *tagów* do wyróżniania tekstu.|  
|[Przewodnik: tworzenie konspektu](../extensibility/walkthrough-outlining.md)|Pokazuje, jak dodać konspekt dla określonych rodzajów nawiasów klamrowych.|  
|[Przewodnik: wyświetlanie parowanych nawiasów klamrowych](../extensibility/walkthrough-displaying-matching-braces.md)|Pokazuje, w jaki sposób podświetlić pasujące nawiasy klamrowe.|  
|[Przewodnik: wyświetlanie etykietek narzędzi SzybkieInfo](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)|Pokazuje sposób wyświetlania okien podręcznych sekcji szybkich informacji, które opisują elementy kodu, takie jak właściwości, metody i zdarzenia.|  
|[Przewodnik: wyświetlanie pomocy dotyczącej sygnatur](../extensibility/walkthrough-displaying-signature-help.md)|Pokazuje, jak wyświetlić okna podręczne, które zawierają informacje o liczbie i typach parametrów w podpisie.|  
|[Przewodnik: wyświetlanie uzupełniania instrukcji](../extensibility/walkthrough-displaying-statement-completion.md)|Pokazuje, jak zaimplementować uzupełnianie instrukcji.|  
|[Przewodnik: implementowanie fragmentów kodu](../extensibility/walkthrough-implementing-code-snippets.md)|Pokazuje, jak zaimplementować rozszerzanie fragmentów kodu.|  
|[Przewodnik: wyświetlanie sugestii „żarówka”](../extensibility/walkthrough-displaying-light-bulb-suggestions.md)|Pokazuje, jak wyświetlić żarówki dla sugestii kodu.|  
|[Przewodnik: używanie polecenia programu PowerShell z rozszerzeniem edytora](../extensibility/walkthrough-using-a-shell-command-with-an-editor-extension.md)|Pokazuje, jak skojarzyć polecenie menu w pakietu VSPackage ze składnikiem MEF.|  
|[Przewodnik: używanie klawisza skrótu z rozszerzeniem edytora](../extensibility/walkthrough-using-a-shortcut-key-with-an-editor-extension.md)|Pokazuje, jak skojarzyć skrót menu w pakietu VSPackage ze składnikiem MEF.|  
|[Managed Extensibility Framework (MEF)](https://msdn.microsoft.com/library/6c61b4ec-c6df-4651-80f1-4854f8b14dde)|Zawiera informacje o Managed Extensibility Framework (MEF).|  
|[Windows Presentation Foundation](https://msdn.microsoft.com/library/f667bd15-2134-41e9-b4af-5ced6fafab5d)|Zawiera informacje o Windows Presentation Foundation (WPF).|  
  
## <a name="reference"></a>Dokumentacja  
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
