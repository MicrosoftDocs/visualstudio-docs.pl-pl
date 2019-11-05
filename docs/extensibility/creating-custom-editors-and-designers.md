---
title: Tworzenie edytorów niestandardowych i projektantów | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- designers [Visual Studio SDK]
- editors [Visual Studio SDK], custom
ms.assetid: b6a5e8b2-0ae1-4fc3-812d-09d40051b435
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7a6cb0d70566eaabb2ba37cb209041e03684c958
ms.sourcegitcommit: 97623fd6190c43fed0d2ee7af92b01c375282622
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/04/2019
ms.locfileid: "73568893"
---
# <a name="create-custom-editors-and-designers"></a>Tworzenie niestandardowych edytorów i projektantów

Zintegrowane środowisko programistyczne (IDE) programu Visual Studio może obsługiwać różne typy edytorów:

- Visual Studio Core Editor

- Edytory niestandardowe

- Edytory zewnętrzne

- Projektanci

Poniższe informacje ułatwiają wybranie typu edytora, którego potrzebujesz.

## <a name="types-of-editor"></a>Typy edytora

Aby uzyskać informacje na temat edytora podstawowego programu Visual Studio, zobacz sekcję [poszerzanie edytora i usług językowych](../extensibility/extending-the-editor-and-language-services.md).

### <a name="custom-editors"></a>Edytory niestandardowe
 Edytor niestandardowy to ten, który jest przeznaczony do pracy w wyspecjalizowanych warunkach. Można na przykład utworzyć Edytor, którego funkcja ma odczytywać i zapisywać dane w określonym repozytorium, takim jak program Microsoft Exchange Server. Wybierz Edytor niestandardowy, jeśli chcesz, aby Edytor współdziałał z typem projektu, lub jeśli chcesz, aby Edytor miał tylko kilka określonych poleceń. Należy jednak pamiętać, że użytkownicy nie będą mogli edytować standardowych projektów [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] przy użyciu niestandardowego edytora.

 Edytor niestandardowy może użyć fabryki edytora i dodać informacje o Edytorze do rejestru. Jednak typ projektu skojarzony z edytorem niestandardowym może tworzyć wystąpienia edytora niestandardowego w inny sposób.

 Edytor niestandardowy może użyć aktywacji w miejscu lub uproszczonego osadzania w celu zaimplementowania widoku.

### <a name="external-editors"></a>Edytory zewnętrzne
 Edytory zewnętrzne to edytory, które nie są zintegrowane z programem Visual Studio, takie jak Microsoft Word, Notepad lub Microsoft FrontPage. Możesz wywołać taki Edytor, jeśli na przykład przekazujesz do niego tekst z pakietu VSPackage. Edytory zewnętrzne rejestrują się i mogą być używane poza programem Visual Studio. Gdy wywołujesz zewnętrzny edytor i można go osadzić w oknie hosta, pojawia się w oknie w IDE. W przeciwnym razie IDE tworzy osobne okno.

 Metoda <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> ustawia priorytet dokumentu przy użyciu wyliczenia <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY>. Jeśli `DP_External` wartość jest określona, plik może być otwarty przez zewnętrzny edytor.

## <a name="editor-design-decisions"></a>Decyzje projektowe edytora
 Poniższe pytania dotyczące projektowania ułatwią wybranie typu edytora najlepiej dopasowanego do aplikacji:

- Czy aplikacja będzie zapisywać swoje dane w plikach, czy nie? Czy dane będą zapisywane w plikach, czy będą one w formacie standardowym, czy standardowym?

   Jeśli używasz standardowego formatu plików, inne typy projektów oprócz projektu będą mogły otwierać i odczytywać i zapisywać dane. Jeśli używasz niestandardowego formatu pliku, jednak tylko typ projektu będzie mógł otwierać i odczytywać i zapisywać dane.

   Jeśli projekt używa plików, należy dostosować standardowy Edytor. Jeśli projekt nie korzysta z plików, ale zamiast tego używa elementów w bazie danych lub innym repozytorium, należy utworzyć niestandardowy Edytor.

- Czy Edytor musi hostować kontrolki ActiveX?

   Jeśli Edytor obsługuje kontrolki ActiveX, zaimplementuj Edytor aktywacji w miejscu, jak opisano w [aktywacji w miejscu](/visualstudio/misc/in-place-activation?view=vs-2015). Jeśli nie obsługuje kontrolek ActiveX, należy użyć uproszczonego edytora osadzania lub dostosować [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] domyślnego edytora.

- Czy Edytor będzie obsługiwał wiele widoków? Jeśli chcesz, aby widoki edytora były widoczne w tym samym czasie co domyślny edytor, musisz obsługiwać wiele widoków.

   Jeśli Edytor musi obsługiwać wiele widoków, dane dokumentu i obiekty widoku dokumentu dla edytora muszą być oddzielnymi obiektami. Aby uzyskać więcej informacji, zobacz [Obsługa widoków wielu dokumentów](../extensibility/supporting-multiple-document-views.md).

   Jeśli Edytor obsługuje wiele widoków, czy planujesz użyć implementacji buforu tekstowego [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Core (<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> Object) dla obiektu danych dokumentu? Oznacza to, że chcesz obsługiwać widok edytora obok siebie przy użyciu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Core Editor? Jest to podstawą projektanta formularzy.

- Jeśli musisz hostować zewnętrzny edytor, czy edytor ma być osadzony w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]?

   Jeśli może być osadzony, należy utworzyć okno hosta dla edytora zewnętrznego, a następnie wywołać metodę <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> i ustawić wartość wyliczenia <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> na `DP_External`. Jeśli Edytor nie może być osadzony, środowisko IDE automatycznie utworzy osobne okno.

## <a name="in-this-section"></a>W tej sekcji

[Przewodnik: Tworzenie niestandardowego edytora](../extensibility/walkthrough-creating-a-custom-editor.md)\
Wyjaśnia, jak utworzyć Edytor niestandardowy.

[Przewodnik: Dodawanie funkcji do niestandardowego edytora](../extensibility/walkthrough-adding-features-to-a-custom-editor.md)\
Wyjaśnia, jak dodać funkcje do niestandardowego edytora.

[Inicjowanie projektanta i konfiguracja metadanych](../extensibility/designer-initialization-and-metadata-configuration.md)\
Wyjaśnia, jak zainicjować projektanta.

[Dostarcz obsługę cofania dla projektantów](../extensibility/supplying-undo-support-to-designers.md)\
Wyjaśnia, jak zapewnić obsługę cofania dla projektantów.

[Kolorowanie składni w edytorach niestandardowych](../extensibility/syntax-coloring-in-custom-editors.md)\
Wyjaśnia różnicę między kolorami składni w edytorze podstawowym i w edytorach niestandardowych.

[Dane dokumentu i widok dokumentu w edytorach niestandardowych](../extensibility/document-data-and-document-view-in-custom-editors.md)\
Wyjaśnia, jak zaimplementować dane dokumentu i widoki dokumentów w edytorach niestandardowych.

## <a name="related-sections"></a>Sekcje pokrewne

[Starsze interfejsy w edytorze](/visualstudio/extensibility/legacy-interfaces-in-the-editor?view=vs-2015)\
Wyjaśnia, jak uzyskać dostęp do podstawowego edytora za pomocą starszego interfejsu API.

[Opracowywanie starszej wersji usługi językowej](../extensibility/internals/developing-a-legacy-language-service.md)\
Wyjaśnia sposób implementacji usługi językowej.

[Rozciągnij inne części programu Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)\
Wyjaśnia, jak tworzyć elementy interfejsu użytkownika, które pasują do pozostałej części [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>