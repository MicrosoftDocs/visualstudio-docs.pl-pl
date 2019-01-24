---
title: W edytorze podstawowych | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - core editor
ms.assetid: 8265f31c-c45b-4858-882c-6d9f1e3b9083
caps.latest.revision: 22
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 61484c9d01022b9f3b860f0c7b78dd3aedc045f4
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54794848"
---
# <a name="inside-the-core-editor"></a>W edytorze podstawowych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Edytorze podstawowych funkcji to zbiór kilka składników, które pozwalają na modyfikowanie i wykonywania zapytań względem informacji tekstowych. Jeśli dostosowano podstawowy edytor przy użyciu starszej wersji interfejsu API, można nadal używać tych dostosowania, które będą kierowane za pośrednictwem karty edytora. Jest to zalecane, jednak dostosować własne dostosowania do edytora nowego interfejsu API.  
  
 Niektórych ważnych aspektów podstawowy edytor kwestie:  
  
-   Bufor tekstowy  
  
-   Widok tekstu  
  
-   W oknie kodu  
  
-   Znaczniki tekstu  
  
-   Menedżer tekstu  
  
-   Integracja z usługami języka  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Tworzenie wystąpienia edytora podstawowego przy użyciu starszej wersji interfejsu API](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)  
 Instrukcje krok po kroku dotyczące sposobu korzystania <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> do utworzenia wystąpienia podstawowego edytora.  
  
 [Uzyskiwanie dostępu do buforu tekstowego przy użyciu starszego interfejsu API](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md)  
 W tym artykule omówiono rolę buforu tekstu w edytorze podstawowych, wyjaśnia skojarzone systemów, które umożliwiają dostęp do buforu i zawiera listę interfejsów implementowanych przez obiekt buforu tekstu, <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>.  
  
 [Zdarzenia buforu tekstowego w starszym interfejsie API](../extensibility/text-buffer-events-in-the-legacy-api.md)  
 Zawiera listę interfejsów, które są używane dla powiadomień o zdarzeniach buforu tekstu.  
  
 [Instrukcje: Rejestrowanie zdarzeń buforu tekstu przy użyciu starszej wersji interfejsu API](../extensibility/how-to-register-for-text-buffer-events-with-the-legacy-api.md)  
 Opisuje sposób poinformowania zdarzenia buforu tekstu.  
  
 [Używanie menedżera tekstu do monitorowania ustawień globalnych](../extensibility/using-the-text-manager-to-monitor-global-settings.md)  
 W tym artykule omówiono sposób Menedżer tekstu jest używany do udostępniania informacji preferencji globalnych podstawowe składniki edytora i jak otrzymywać powiadomienia o zdarzeniach Menedżer tekstu.  
  
 [Uzyskiwanie dostępu do widoku tekstowego przy użyciu starszego interfejsu API](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)  
 W tym artykule opisano rolę widoku tekstu w edytorze podstawowych i wyświetla interfejsy implementowane przez <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> obiektu.  
  
 [Dostosowywanie okien kodu za pomocą starszego interfejsu API](../extensibility/customizing-code-windows-by-using-the-legacy-api.md)  
 Zawiera informacje dotyczące sposobu okna kodu jest używane, aby ująć widoku tekstu, w tym artykule omówiono, jak Menedżer okien kod służy do zapewnienia dekoracje do okna kodu i zapewnia powiadomienia o nowych widoków.  
  
 [Zmienianie ustawień widoku za pomocą starszego interfejsu API](../extensibility/changing-view-settings-by-using-the-legacy-api.md)  
 Instrukcje krok po kroku dotyczące wymusić ustawienia wyświetlania i usuwania ustawień wymuszone.  
  
 [Usługi językowe oraz edytor podstawowy](../extensibility/language-services-and-the-core-editor.md)  
 W tym artykule opisano tworzenie wystąpienia usługi języka w celu kontroli kodu dekoracje.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Przewodnik: Tworzenie edytorze podstawowych i rejestrowanie typu pliku w edytorze](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md)  
 Instrukcje krok po kroku dotyczące uruchamiania podstawowy edytor z kodu zarządzanego.  
  
 [Pasek list rozwijanych](../extensibility/drop-down-bar.md)  
 W tym artykule omówiono sposób pasek listy rozwijanej jest używana w oknie kodu i opisano interfejsy, które są używane podczas implementowania pasek listy rozwijanej.  
  
 [Korzystanie ze znaczników tekstu ze starszym interfejsem API](../extensibility/using-text-markers-with-the-legacy-api.md)  
 Wyjaśnia pojęcie znaczników tekstu i jak są one używane w edytorze podstawowych i wyświetla listę interfejsów, które są używane do dostępu i zarządzania znaczników tekstu.  
  
 [Instrukcje: Dodaj znaczniki standardowy tekst](../extensibility/how-to-add-standard-text-markers.md)  
 Instrukcje krok po kroku dotyczące tworzenia znacznika tekstu i Dodaj polecenie niestandardowe do menu skrótów.  
  
 [Instrukcje: Tworzenie niestandardowego tekstu znaczników](../extensibility/how-to-create-custom-text-markers.md)  
 Instrukcje krok po kroku dotyczące tworzenia znacznika niestandardowego tekstu i podać typ znacznika jako usługa.
