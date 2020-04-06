---
title: Rozszerzanie edytora i usług językowych | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new -
ms.assetid: 8d04f8db-eda7-4b3e-b6eb-c06df104502a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 239c638ec32cc0dc2b2e275a5dbe0c4213a3423e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711711"
---
# <a name="extend-the-editor-and-language-services"></a>Rozszerzanie usług edytora i języka
Można dodać funkcje usługi języka (takie jak IntelliSense) do własnego edytora i rozszerzyć większość funkcji edytora kodu programu Visual Studio.  Aby uzyskać pełną listę tego, co można rozszerzyć, zobacz [Usługi językowe i punkty rozszerzeń edytora](../extensibility/language-service-and-editor-extension-points.md).

 Rozszerzyć większość funkcji edytora przy użyciu managed extensibility framework (MEF). Na przykład, jeśli funkcją edytora, którą chcesz rozszerzyć, jest kolorowanie składni, można napisać *część komponentu* MEF, która definiuje klasyfikacje, dla których ma być różne kolorowanie i sposób ich obsługi. Edytor obsługuje również wiele rozszerzeń tej samej funkcji.

 Warstwa prezentacji edytora jest oparta na programie Windows Presentation Framework (WPF). WPF WPF udostępnia bibliotekę grafiki do elastycznego formatowania tekstu, a także zapewnia wizualizacje, takie jak grafiki i animacje.

 Visual Studio SDK udostępnia karty znane jako *podkładki* do obsługi vsPackages, które zostały napisane dla wcześniejszych wersji. Niemniej jednak jeśli masz istniejący vsPackage, zaleca się zaktualizować go do nowej technologii w celu uzyskania lepszej wydajności i niezawodności.

## <a name="related-topics"></a>Tematy pokrewne

|Tytuł|Opis|
|-----------|-----------------|
|[Wprowadzenie do usług językowych i rozszerzeń edytora](../extensibility/getting-started-with-language-service-and-editor-extensions.md)|W tym artykule wyjaśniono, jak utworzyć rozszerzenie do edytora.|
|[Wewnątrz edytora](../extensibility/inside-the-editor.md)|Opisuje ogólną strukturę edytora i wyświetla niektóre z jego funkcji.|
|[Zarządzane ramy rozszerzalności w edytorze](../extensibility/managed-extensibility-framework-in-the-editor.md)|W tym artykule wyjaśniono, jak używać managed extensibility framework (MEF) z edytorem.|
|[Punkty rozszerzeń usługi językowej i edytora](../extensibility/language-service-and-editor-extension-points.md)|Wyświetla listę punktów rozszerzenia edytora. Punkty rozszerzeń reprezentują funkcje edytora, które można rozszerzyć.|
|[Przewodnik: Tworzenie ozdabiania widoku, poleceń i ustawień (prowadnice kolumn)](../extensibility/walkthrough-creating-a-view-adornment-commands-and-settings-column-guides.md)|Przechodzi przez i wyjaśnia tworzenie ozdabiania widoku, który rysuje linie pomocnicze kolumny, aby ułatwić utrzymanie kodu do określonej szerokości wyświetlania.  Pokazuje również ustawienia odczytu i zapisu, a także deklarowanie i implementowanie poleceń, które można wywołać z okna polecenia.|
|[Importowanie edytora](../extensibility/editor-imports.md)|Wyświetla listę usług, które rozszerzenie można zaimportować.|
|[Dostosowywanie starszego kodu do edytora](/visualstudio/extensibility/adapting-legacy-code-to-the-editor?view=vs-2015)|W tym artykule wyjaśniono różne sposoby dostosowania starszego kodu (przed programem Visual Studio 2010), aby rozszerzyć edytor.|
|[Migrowanie starszej usługi językowej](../extensibility/internals/migrating-a-legacy-language-service.md)|W tym artykule wyjaśniono, jak przeprowadzić migrację usługi języka opartej na pakiecie VSPackage.|
|[Instruktaż: łączenie typu zawartości z rozszerzeniem nazwy pliku](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)|Pokazuje, jak połączyć typ zawartości z rozszerzeniem nazwy pliku.|
|[Instruktaż: tworzenie glifów marginesu](../extensibility/walkthrough-creating-a-margin-glyph.md)|Pokazuje, jak dodać ikonę do marginesu.|
|[Instruktaż: Wyróżnianie tekstu](../extensibility/walkthrough-highlighting-text.md)|Pokazuje, jak używać *znaczników* do wyróżniania tekstu.|
|[Przewodnik: Dodawanie tworzenia](../extensibility/walkthrough-outlining.md)|Pokazuje, jak dodać tworzenie nakreślenia dla określonych rodzajów nawiasów klamrowych.|
|[Instruktaż: Wyświetlanie pasujących nawiasów klamrowych](../extensibility/walkthrough-displaying-matching-braces.md)|Pokazuje, jak wyróżnić pasujące nawiasy klamrowe.|
|[Instruktaż: Wyświetlanie etykietek narzędzi QuickInfo](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)|Pokazuje, jak wyświetlić wyskakujące okienka QuickInfo, które opisują elementy kodu, takie jak właściwości, metody i zdarzenia.|
|[Instruktaż: Wyświetlanie pomocy dotycząca podpisu](../extensibility/walkthrough-displaying-signature-help.md)|Pokazuje sposób wyświetlania wyskakujących okienków, które podają informacje o liczbie i typach parametrów w podpisie.|
|[Instruktaż: Zakończenie instrukcji wyświetlania](../extensibility/walkthrough-displaying-statement-completion.md)|Pokazuje, jak zaimplementować zakończenie instrukcji.|
|[Instruktaż: Implementowanie fragmentów kodu](../extensibility/walkthrough-implementing-code-snippets.md)|Pokazuje, jak zaimplementować rozszerzenie fragmentu kodu.|
|[Instruktaż: Wyświetlanie sugestii żarówki](../extensibility/walkthrough-displaying-light-bulb-suggestions.md)|Pokazuje, jak wyświetlać żarówki dla sugestii kodu.|
|[Instruktaż: używanie polecenia powłoki z rozszerzeniem edytora](../extensibility/walkthrough-using-a-shell-command-with-an-editor-extension.md)|Pokazuje, jak skojarzyć polecenie menu w vspackage ze składnikiem MEF.|
|[Instruktaż: używanie klawisza skrótu z rozszerzeniem edytora](../extensibility/walkthrough-using-a-shortcut-key-with-an-editor-extension.md)|Pokazuje, jak skojarzyć skrót menu w vspackage ze składnikiem MEF.|
|[Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index)|Zawiera informacje na temat zarządzanej struktury rozszerzalności (MEF).|
|[Windows Presentation Foundation](/dotnet/framework/wpf/index)|Zawiera informacje o fundacji Prezentacji systemu Windows (WPF).|

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
