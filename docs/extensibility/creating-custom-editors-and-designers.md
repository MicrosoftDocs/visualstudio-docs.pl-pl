---
title: Tworzenie edytorów niestandardowych i projektantów | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- designers [Visual Studio SDK]
- editors [Visual Studio SDK], custom
ms.assetid: b6a5e8b2-0ae1-4fc3-812d-09d40051b435
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9177e6f431eb24a337822dd7de0a0b9586e1de0e
ms.sourcegitcommit: ba966327498a0f67d2df2291c60b62312f40d1d3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/06/2020
ms.locfileid: "93414259"
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
 Edytor niestandardowy to ten, który jest przeznaczony do pracy w wyspecjalizowanych warunkach. Można na przykład utworzyć Edytor, którego funkcja ma odczytywać i zapisywać dane w określonym repozytorium, takim jak program Microsoft Exchange Server. Wybierz Edytor niestandardowy, jeśli chcesz, aby Edytor współdziałał z typem projektu, lub jeśli chcesz, aby Edytor miał tylko kilka określonych poleceń. Należy jednak pamiętać, że użytkownicy nie będą mogli edytować standardowych projektów przy użyciu niestandardowego edytora [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

 Edytor niestandardowy może użyć fabryki edytora i dodać informacje o Edytorze do rejestru. Jednak typ projektu skojarzony z edytorem niestandardowym może tworzyć wystąpienia edytora niestandardowego w inny sposób.

 Edytor niestandardowy może użyć aktywacji w miejscu lub uproszczonego osadzania w celu zaimplementowania widoku.

### <a name="external-editors"></a>Edytory zewnętrzne
 Edytory zewnętrzne to edytory, które nie są zintegrowane z programem Visual Studio, takie jak Microsoft Word, Notepad lub Microsoft FrontPage. Możesz wywołać taki Edytor, jeśli na przykład przekazujesz do niego tekst z pakietu VSPackage. Edytory zewnętrzne rejestrują się i mogą być używane poza programem Visual Studio. Gdy wywołujesz zewnętrzny edytor i można go osadzić w oknie hosta, pojawia się w oknie w IDE. W przeciwnym razie IDE tworzy osobne okno.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>Metoda ustawia priorytet dokumentu przy użyciu <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> wyliczenia. Jeśli `DP_External` wartość jest określona, plik może być otwarty przez zewnętrzny edytor.

## <a name="editor-design-decisions"></a>Decyzje projektowe edytora
 Poniższe pytania dotyczące projektowania ułatwią wybranie typu edytora najlepiej dopasowanego do aplikacji:

- Czy aplikacja będzie zapisywać swoje dane w plikach, czy nie? Czy dane będą zapisywane w plikach, czy będą one w formacie standardowym, czy standardowym?

   Jeśli używasz standardowego formatu plików, inne typy projektów oprócz projektu będą mogły otwierać i odczytywać i zapisywać dane. Jeśli używasz niestandardowego formatu pliku, jednak tylko typ projektu będzie mógł otwierać i odczytywać i zapisywać dane.

   Jeśli projekt używa plików, należy dostosować standardowy Edytor. Jeśli projekt nie korzysta z plików, ale zamiast tego używa elementów w bazie danych lub innym repozytorium, należy utworzyć niestandardowy Edytor.

- Czy Edytor musi hostować kontrolki ActiveX?

   Jeśli Edytor obsługuje kontrolki ActiveX, zaimplementuj Edytor aktywacji w miejscu, jak opisano w [aktywacji w miejscu](/previous-versions/visualstudio/visual-studio-2015/misc/in-place-activation?preserve-view=true&view=vs-2015). Jeśli nie hostuje formantów ActiveX, użyj uproszczonego edytora osadzania lub Dostosuj [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Edytor domyślny.

- Czy Edytor będzie obsługiwał wiele widoków? Jeśli chcesz, aby widoki edytora były widoczne w tym samym czasie co domyślny edytor, musisz obsługiwać wiele widoków.

   Jeśli Edytor musi obsługiwać wiele widoków, dane dokumentu i obiekty widoku dokumentu dla edytora muszą być oddzielnymi obiektami. Aby uzyskać więcej informacji, zobacz [Obsługa widoków wielu dokumentów](../extensibility/supporting-multiple-document-views.md).

   Czy edytor obsługuje wiele widoków, czy planujesz używać [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] implementacji buforu tekstowego podstawowego edytora ( <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> Object) dla obiektu danych dokumentu? Oznacza to, że chcesz obsługiwać widok edytora obok siebie przy użyciu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] podstawowego edytora? Jest to podstawą projektanta formularzy.

- Jeśli chcesz hostować zewnętrzny edytor, czy edytor ma być osadzony wewnątrz [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ?

   Jeśli może być osadzony, należy utworzyć okno hosta dla edytora zewnętrznego, a następnie wywołać <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> metodę i ustawić <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> wartość wyliczenia na `DP_External` . Jeśli Edytor nie może być osadzony, środowisko IDE automatycznie utworzy osobne okno.

## <a name="in-this-section"></a>W tej sekcji

[Przewodnik: Tworzenie edytora niestandardowego](../extensibility/walkthrough-creating-a-custom-editor.md)\
Wyjaśnia, jak utworzyć Edytor niestandardowy.

[Przewodnik: Dodawanie funkcji do edytora niestandardowego](../extensibility/walkthrough-adding-features-to-a-custom-editor.md)\
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

[Starsze interfejsy w edytorze](/previous-versions/visualstudio/visual-studio-2015/extensibility/legacy-interfaces-in-the-editor?preserve-view=true&view=vs-2015)\
Wyjaśnia, jak uzyskać dostęp do podstawowego edytora za pomocą starszego interfejsu API.

[Opracowywanie starszej wersji usługi językowej](../extensibility/internals/developing-a-legacy-language-service.md)\
Wyjaśnia sposób implementacji usługi językowej.

[Rozszerzając inne części programu Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)\
Wyjaśnia, jak utworzyć elementy interfejsu użytkownika, które pasują do pozostałej części [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>