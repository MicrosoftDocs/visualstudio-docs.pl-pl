---
title: Usługi językowe i podstawowy edytor | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - language services
ms.assetid: e03199a6-ad5f-4075-bfba-8d36865112b7
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1e708ffe796bfc9342bc20c3e7f20d5cf0d05058
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68180304"
---
# <a name="language-services-and-the-core-editor"></a>Usługi językowe oraz edytor podstawowy
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Edytory w programie Visual Studio często są skojarzone z usługą języka. Usługa języka zapewnia między innymi kolorowanie składni, uzupełnianie instrukcji, IntelliSense i formatowanie tekstu.  
  
## <a name="core-editors-and-document-data-objects"></a>Podstawowe edytory i obiekty danych dokumentów  
 Podczas uzyskiwania dostępu do podstawowego edytora nie można tworzyć danych dokumentu ani obiektów widoku dokumentu. IDE tworzy i kontroluje te dwa obiekty i uzyskuje do nich uchwyty, wykonując odpowiednie wywołania w implementacji fabrycznej edytora.  
  
 Aby uzyskać więcej informacji, zobacz [ustalanie, który Edytor otwiera plik w projekcie](../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md).  
  
## <a name="language-services-and-the-core-editor"></a>Usługi językowe oraz edytor podstawowy  
 Implementując usługę języka, można kontrolować sposób wyświetlania danych w widoku dokumentu. Usługa języka zapewnia informacje i zachowanie specyficzne dla danego języka, takie jak Visual C++. Podczas tworzenia bufora tekstu i określania rozszerzenia nazwy pliku dla otwieranego dokumentu bufor tekstowy określa usługę języka skojarzoną z tym rozszerzeniem nazwy pliku z klucza rejestru, HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\Editors \\ {YOURLANGUAGESERVICE GUID} \Extensions. Standardowa procedura ładowania pakietu VSPackage ładuje pakietu VSPackage i tworzy wystąpienie usługi językowej.  
  
 Podstawowa usługa języka jest pokazana na poniższej ilustracji.  
  
 ![Grafika modelu usługi językowej](../extensibility/media/vslanguageservicemodel.gif "vsLanguageServiceModel")  
Podstawowe obiekty edytora i usługi językowej  
  
 Obiekt danych dokumentu dla edytora podstawowego jest nazywany buforem tekstowym i jest reprezentowany przez <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> obiekt. Obiekt widoku dokumentu jest nazywany widokiem tekstu i jest reprezentowany przez <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow> obiekt. Te dwa obiekty współpracują z usługą języka w celu zapewnienia ujednoliconego widoku podstawowego edytora. Informacje z bufora tekstu i widoku tekstu są wyświetlane w oknie dokumentu o nazwie okno kodu. Dokument okna kod jest zarządzany przez Menedżera okna kodu.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow>   
 [Udostępnianie kontekstu usługi językowej przy użyciu starszego interfejsu API](../extensibility/providing-a-language-service-context-by-using-the-legacy-api.md)   
 [Hosting IntelliSense](../extensibility/intellisense-hosting.md)   
 [Języki zawarte](../extensibility/contained-languages.md)   
 [Tworzenie starszej wersji usługi językowej](../extensibility/internals/developing-a-legacy-language-service.md)
