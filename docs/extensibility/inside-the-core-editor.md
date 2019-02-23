---
title: W edytorze podstawowych | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - core editor
ms.assetid: 8265f31c-c45b-4858-882c-6d9f1e3b9083
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 81d91603d6c365946b1064cac3a7f1ca3c1e6ba8
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56713298"
---
# <a name="inside-the-core-editor"></a>W edytorze podstawowych
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Edytorze podstawowych funkcji to zbiór kilka składników, które pozwalają na modyfikowanie i wykonywania zapytań względem informacji tekstowych. Jeśli dostosowano podstawowy edytor przy użyciu starszej wersji interfejsu API, można nadal używać tych dostosowania, które będą kierowane za pośrednictwem karty edytora. Jest to zalecane, jednak dostosować własne dostosowania do edytora nowego interfejsu API.

 Niektórych ważnych aspektów podstawowy edytor kwestie:

-   Bufor tekstowy

-   Widok tekstu

-   W oknie kodu

-   Znaczniki tekstu

-   Menedżer tekstu

-   Integracja z usługami języka

## <a name="in-this-section"></a>W tej sekcji
- [Utwórz wystąpienie podstawowy edytor przy użyciu starszej wersji interfejsu API](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md) instrukcje krok po kroku dotyczące sposobu korzystania <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> do utworzenia wystąpienia podstawowego edytora.

- [Dostęp do buforu tekstowego przy użyciu starszej wersji interfejsu API](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md) w tym artykule omówiono rolę buforu tekstu w edytorze podstawowych, wyjaśnia skojarzone systemów, które umożliwiają dostęp do buforu i zawiera listę interfejsów implementowanych przez obiekt buforu tekstu, <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>.

- [Zdarzenia buforu tekstu w starszej wersji interfejsu API](../extensibility/text-buffer-events-in-the-legacy-api.md) zawiera listę interfejsów, które są używane dla powiadomień o zdarzeniach buforu tekstu.

- [Instrukcje: Zarejestruj się, aby zdarzenia buforu tekstu przy użyciu starszej wersji interfejsu API](../extensibility/how-to-register-for-text-buffer-events-with-the-legacy-api.md) opisuje sposób poinformowania zdarzenia buforu tekstu.

- [Ustawienia globalne monitorowanie za pomocą Menedżera tekstu](../extensibility/using-the-text-manager-to-monitor-global-settings.md) w tym artykule omówiono sposób Menedżer tekstu jest używany do udostępniania informacji preferencji globalnych podstawowe składniki edytora i jak otrzymywać powiadomienia o zdarzeniach Menedżer tekstu.

- [Dostęp do widoku theText przy użyciu starszej wersji interfejsu API](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md) opisano rolę widoku tekstu w edytorze podstawowych i wyświetla interfejsy implementowane przez <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> obiektu.

- [Dostosowywanie kodu systemu windows przy użyciu starszej wersji interfejsu API](../extensibility/customizing-code-windows-by-using-the-legacy-api.md) zawiera informacje o oknie kodu jest używane, aby ująć widoku tekstu, w tym artykule omówiono, jak Menedżer okien kod służy do zapewnienia dekoracje do okna kodu i zawiera powiadomienia o nowych widoków .

- [Zmień ustawienia widoku przy użyciu starszej wersji interfejsu API](../extensibility/changing-view-settings-by-using-the-legacy-api.md) zawiera instrukcje krok po kroku dotyczące wymusić ustawienia wyświetlania i usuwania ustawień wymuszone.

- [Usługi języka oraz podstawowy edytor](../extensibility/language-services-and-the-core-editor.md) w tym artykule opisano tworzenie wystąpienia usługi języka w celu kontroli kodu dekoracje.

## <a name="related-sections"></a>Sekcje pokrewne
- [Przewodnik: Tworzenie podstawowej edytora i rejestrując typu pliku w edytorze](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md) zawiera instrukcje krok po kroku dotyczące uruchamiania podstawowy edytor z kodu zarządzanego.

- [Listę rozwijaną paska](../extensibility/drop-down-bar.md) w tym artykule omówiono, jak pasek listy rozwijanej jest używany w oknie kodu i opisano interfejsy, które są używane podczas implementowania pasek listy rozwijanej.

- [Korzystanie ze znaczników tekstu przy użyciu starszej wersji interfejsu API](../extensibility/using-text-markers-with-the-legacy-api.md) wyjaśnia pojęcie znaczników tekstu i jak są one używane w edytorze podstawowych i wyświetla listę interfejsów, które są używane do dostępu i zarządzania znaczników tekstu.

- [Instrukcje: Dodaj znaczniki standardowy tekst](../extensibility/how-to-add-standard-text-markers.md) zawiera instrukcje krok po kroku dotyczące tworzenia znacznika tekstu i Dodaj polecenie niestandardowe do menu skrótów.

- [Instrukcje: Tworzenie niestandardowego tekstu znaczniki](../extensibility/how-to-create-custom-text-markers.md) zawiera szczegółowe instrukcje dotyczące tworzenia znacznika niestandardowego tekstu i podać typ znacznika jako usługa.