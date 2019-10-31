---
title: Rozszerzanie edytora i usług językowych | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new -
ms.assetid: 8d04f8db-eda7-4b3e-b6eb-c06df104502a
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: af1fa0222be9630a495a43204d7a973341190131
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2019
ms.locfileid: "73186668"
---
# <a name="extend-the-editor-and-language-services"></a>Poszerzanie edytora i usług językowych
Funkcje usługi językowej (na przykład IntelliSense) można dodać do własnego edytora i rozłożyć większość funkcji edytora kodu programu Visual Studio.  Aby uzyskać pełną listę elementów, które można rozszerzać, zobacz [punkty rozszerzenia usługi językowej i edytora](../extensibility/language-service-and-editor-extension-points.md).

 Większość funkcji edytora można rozłożyć przy użyciu Managed Extensibility Framework (MEF). Na przykład, jeśli funkcja edytora, która ma zostać rozszerzona, ma kolorowanie składni, można napisać *część składnika* MEF, która definiuje klasyfikacje, dla których ma być różne kolorowanie i w jaki sposób mają być obsługiwane. Edytor obsługuje również wiele rozszerzeń tej samej funkcji.

 Warstwa prezentacji edytora jest oparta na strukturze prezentacji systemu Windows (WPF). WPF udostępnia bibliotekę grafiki do elastycznego formatowania tekstu, a także udostępnia wizualizacje, takie jak grafika i animacje.

 Zestaw Visual Studio SDK zawiera karty, które są nazywane *podkładkami* do obsługi pakietów VSPackage utworzonych dla wcześniejszych wersji. Jeśli jednak masz istniejący pakietu VSPackage, Zalecamy zaktualizowanie go do nowej technologii w celu uzyskania lepszej wydajności i niezawodności.

## <a name="related-topics"></a>Tematy pokrewne

|Tytuł|Opis|
|-----------|-----------------|
|[Wprowadzenie do rozszerzeń usługi językowej i edytora](../extensibility/getting-started-with-language-service-and-editor-extensions.md)|Wyjaśnia, jak utworzyć rozszerzenie dla edytora.|
|[Wewnątrz edytora](../extensibility/inside-the-editor.md)|Zawiera opis ogólnej struktury edytora i zawiera listę jego funkcji.|
|[Managed Extensibility Framework w edytorze](../extensibility/managed-extensibility-framework-in-the-editor.md)|Wyjaśnia, jak używać Managed Extensibility Framework (MEF) z edytorem.|
|[Punkty rozszerzenia usługi językowej i edytora](../extensibility/language-service-and-editor-extension-points.md)|Wyświetla listę punktów rozszerzenia edytora. Punkty rozszerzenia reprezentują funkcje edytora, które można rozszerzyć.|
|[Przewodnik: Tworzenie zakończenia, poleceń i ustawień widoku (prowadnice kolumn)](../extensibility/walkthrough-creating-a-view-adornment-commands-and-settings-column-guides.md)|Instruktaże i objaśniające tworzenie zakończenia tworzenia widoku, który rysuje linie prowadnic kolumn, aby pomóc w zachowaniu kodu do określonej szerokości wyświetlania.  Pokazuje również ustawienia odczytu i zapisu, a także deklarując i implementując polecenia, które można wywołać z okna poleceń.|
|[Importy edytora](../extensibility/editor-imports.md)|Wyświetla listę usług, które mogą importować rozszerzenia.|
|[Dostosowanie starszego kodu do edytora](/visualstudio/extensibility/adapting-legacy-code-to-the-editor?view=vs-2015)|Wyjaśnia różne sposoby adaptacji starszego kodu (wersja wstępna programu Visual Studio 2010) w celu rozbudowania edytora.|
|[Migrowanie starszej wersji usługi językowej](../extensibility/internals/migrating-a-legacy-language-service.md)|Wyjaśnia, w jaki sposób przeprowadzić migrację usługi językowej opartej na pakietu VSPackage.|
|[Przewodnik: łączenie typu zawartości z rozszerzeniem nazwy pliku](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)|Pokazuje, jak połączyć typ zawartości z rozszerzeniem nazwy pliku.|
|[Przewodnik: Tworzenie symbolu marginesu](../extensibility/walkthrough-creating-a-margin-glyph.md)|Pokazuje, jak dodać ikonę do marginesu.|
|[Wskazówki: wyróżnianie tekstu](../extensibility/walkthrough-highlighting-text.md)|Pokazuje, jak używać *tagów* do wyróżniania tekstu.|
|[Przewodnik: Dodawanie konspektu](../extensibility/walkthrough-outlining.md)|Pokazuje, jak dodać konspekt dla określonych rodzajów nawiasów klamrowych.|
|[Przewodnik: wyświetlanie pasujących nawiasów klamrowych](../extensibility/walkthrough-displaying-matching-braces.md)|Pokazuje, w jaki sposób podświetlić pasujące nawiasy klamrowe.|
|[Przewodnik: wyświetlanie etykietek narzędzi sekcji szybkich informacji](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)|Pokazuje sposób wyświetlania okien podręcznych sekcji szybkich informacji, które opisują elementy kodu, takie jak właściwości, metody i zdarzenia.|
|[Przewodnik: Wyświetlanie pomocy dotyczącej podpisu](../extensibility/walkthrough-displaying-signature-help.md)|Pokazuje, jak wyświetlić okna podręczne, które zawierają informacje o liczbie i typach parametrów w podpisie.|
|[Przewodnik: Wyświetlanie instrukcji wyświetlania](../extensibility/walkthrough-displaying-statement-completion.md)|Pokazuje, jak zaimplementować uzupełnianie instrukcji.|
|[Przewodnik: implementowanie fragmentów kodu](../extensibility/walkthrough-implementing-code-snippets.md)|Pokazuje, jak zaimplementować rozszerzanie fragmentów kodu.|
|[Przewodnik: wyświetlanie sugestii żarówki](../extensibility/walkthrough-displaying-light-bulb-suggestions.md)|Pokazuje, jak wyświetlić żarówki dla sugestii kodu.|
|[Przewodnik: Używanie polecenia powłoki z rozszerzeniem edytora](../extensibility/walkthrough-using-a-shell-command-with-an-editor-extension.md)|Pokazuje, jak skojarzyć polecenie menu w pakietu VSPackage ze składnikiem MEF.|
|[Przewodnik: używanie klawisza skrótu z rozszerzeniem edytora](../extensibility/walkthrough-using-a-shortcut-key-with-an-editor-extension.md)|Pokazuje, jak skojarzyć skrót menu w pakietu VSPackage ze składnikiem MEF.|
|[Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index)|Zawiera informacje o Managed Extensibility Framework (MEF).|
|[Windows Presentation Foundation](/dotnet/framework/wpf/index)|Zawiera informacje o Windows Presentation Foundation (WPF).|

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