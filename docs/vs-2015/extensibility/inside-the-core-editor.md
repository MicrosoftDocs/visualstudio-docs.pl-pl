---
title: Wewnątrz edytora podstawowego | Microsoft Docs
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
ms.openlocfilehash: cf9bc42aec3aac5acc996487f99c7e1f29ca252c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68203952"
---
# <a name="inside-the-core-editor"></a>Wewnątrz edytora podstawowego
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Podstawowy edytor to zestaw kilku składników, które umożliwiają modyfikowanie i wykonywanie zapytań dotyczących danych tekstowych. Jeśli Edytor podstawowy został dostosowany przy użyciu starszego interfejsu API, można nadal używać tych dostosowań, które będą kierowane za pośrednictwem adapterów edytora. Zaleca się jednak dostosowanie dostosowań do nowego interfejsu API edytora.  
  
 Następujące obszary są istotnymi aspektami edytora podstawowego:  
  
- Bufor tekstu  
  
- Widok tekstu  
  
- Okno kodu  
  
- Znaczniki tekstu  
  
- Menedżer tekstu  
  
- Integracja z usługami językowymi  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Tworzenie wystąpienia edytora podstawowego przy użyciu starszej wersji interfejsu API](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)  
 Zawiera instrukcje krok po kroku dotyczące <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> tworzenia wystąpienia podstawowego edytora.  
  
 [Uzyskiwanie dostępu do buforu tekstowego przy użyciu starszego interfejsu API](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md)  
 Omawia rolę bufora tekstu w edytorze Core, objaśnia skojarzone systemy, które są używane w celu uzyskania dostępu do buforu i zawiera listę interfejsów implementowanych przez obiekt buforu tekstu <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> .  
  
 [Zdarzenia buforu tekstowego w starszym interfejsie API](../extensibility/text-buffer-events-in-the-legacy-api.md)  
 Zawiera listę interfejsów, które są używane do powiadamiania o zdarzeniach buforu tekstu.  
  
 [Instrukcje: rejestrowanie w zdarzeniach buforu tekstowego przy użyciu starszego interfejsu API](../extensibility/how-to-register-for-text-buffer-events-with-the-legacy-api.md)  
 Opisuje sposób doradzania zdarzeń buforu tekstu.  
  
 [Używanie menedżera tekstu do monitorowania ustawień globalnych](../extensibility/using-the-text-manager-to-monitor-global-settings.md)  
 W tym artykule omówiono sposób używania Menedżera tekstów do udostępniania globalnych informacji o preferencjach za pomocą podstawowych składników edytora oraz sposobu otrzymywania powiadomień o zdarzeniach Menedżera tekstu.  
  
 [Uzyskiwanie dostępu do widoku tekstowego przy użyciu starszego interfejsu API](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)  
 Opisuje rolę widoku tekstu w edytorze podstawowym i wyświetla listę interfejsów implementowanych przez <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> obiekt.  
  
 [Dostosowywanie okien kodu za pomocą starszego interfejsu API](../extensibility/customizing-code-windows-by-using-the-legacy-api.md)  
 Zawiera informacje o tym, w jaki sposób okno kodu jest używane do otaczania widoku tekstu, w tym artykule omówiono sposób, w jaki Menedżer okien kodu służy do dostarczania dekoracji do okna kodu i zapewnia powiadomienia o nowych widokach.  
  
 [Zmienianie ustawień widoku za pomocą starszego interfejsu API](../extensibility/changing-view-settings-by-using-the-legacy-api.md)  
 Zawiera instrukcje krok po kroku dotyczące wymuszania ustawień widoku oraz sposobu usuwania ustawień wymuszonych.  
  
 [Usługi językowe oraz edytor podstawowy](../extensibility/language-services-and-the-core-editor.md)  
 Opisuje tworzenie wystąpienia usługi językowej w celu kontrolowania dekoracji kodu.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Przewodnik: tworzenie edytora podstawowego i rejestrowanie typu pliku edytora](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md)  
 Zawiera instrukcje krok po kroku dotyczące sposobu uruchamiania edytora podstawowego z kodu zarządzanego.  
  
 [Pasek list rozwijanych](../extensibility/drop-down-bar.md)  
 Omawia, w jaki sposób pasek rozwijany jest używany w oknie kodu i opisuje interfejsy, które są używane podczas implementowania paska listy rozwijanej.  
  
 [Korzystanie ze znaczników tekstu ze starszym interfejsem API](../extensibility/using-text-markers-with-the-legacy-api.md)  
 Wyjaśnia koncepcję znaczników tekstu i sposobu ich używania w edytorze podstawowym, a także Wyświetla interfejsy, które są używane do uzyskiwania dostępu do znaczników tekstu i zarządzania nimi.  
  
 [Instrukcje: dodawanie standardowych znaczników tekstu](../extensibility/how-to-add-standard-text-markers.md)  
 Zawiera instrukcje krok po kroku dotyczące sposobu tworzenia znacznika tekstu i sposobu dodawania niestandardowego polecenia do menu skrótów.  
  
 [Instrukcje: tworzenie niestandardowych znaczników tekstu](../extensibility/how-to-create-custom-text-markers.md)  
 Zawiera instrukcje krok po kroku dotyczące sposobu tworzenia niestandardowego znacznika tekstu oraz sposobu dostarczania typu znacznika jako usługi.
