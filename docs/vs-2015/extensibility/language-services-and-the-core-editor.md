---
title: Usługi języka oraz podstawowy edytor | Dokumentacja firmy Microsoft
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
- editors [Visual Studio SDK], legacy - language services
ms.assetid: e03199a6-ad5f-4075-bfba-8d36865112b7
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 503924f435dda2d4432c915f9566846f0f4dd964
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51727302"
---
# <a name="language-services-and-the-core-editor"></a>Usługi języka oraz podstawowy edytor
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Edytory w programie Visual Studio są często skojarzone z usługą language. Między innymi usługi językowej zapewnia kolorowanie składni, uzupełniania instrukcji, funkcja IntelliSense i formatowania tekstu.  
  
## <a name="core-editors-and-document-data-objects"></a>Edytory podstawowe i obiekty danych dokumentu  
 Gdy uzyskujesz dostęp do edytora podstawowych, nie należy tworzyć dane dokumentu i obiektów widoku dokumentu. IDE tworzy i kontroluje te dwa obiekty i można uzyskać dojścia do nich, wprowadzając odpowiednie wywołania w edytorze fabryki implementacji.  
  
 Aby uzyskać więcej informacji, zobacz [określająca, które edytora otwiera plik w projekcie](../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md).  
  
## <a name="language-services-and-the-core-editor"></a>Usługi języka oraz podstawowy edytor  
 Przez zaimplementowanie usługi językowej, można kontrolować sposób wyświetlania danych w widoku dokumentu. Usługa języka zawiera informacje i zachowanie, które są specyficzne dla danego języka, takich jak Visual C++. Kiedy utworzyć buforu tekstu i określić rozszerzenie nazwy pliku dla dokumentu, który jest otwierany, bufor tekstowy określa usługa językowa skojarzony z tym rozszerzeniem nazwy pliku z klucza rejestru, HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Editors \\\Extensions {YourLanguageService GUID}. Standardowa pakietu VSPackage, następnie ładowania procedury ładowania usługi pakietu VSPackage i tworzone jest wystąpienie usługi języka.  
  
 Usługa podstawowy język jest wyświetlany na poniższej ilustracji.  
  
 ![Grafika przedstawiająca usługi Model języka](../extensibility/media/vslanguageservicemodel.gif "vsLanguageServiceModel")  
Obiekty usługi podstawowej Edytor i język  
  
 Obiekt danych dokumentu na podstawowy edytor nosi nazwę bufor tekstowy i jest reprezentowana przez <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> obiektu. Obiekt widoku dokumentu nosi nazwę widoku tekstu i jest reprezentowana przez <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow> obiektu. Te dwa obiekty współpracują ze sobą za pośrednictwem usługi języka, aby zapewnić spójny widok podstawowy edytor. Informacje z buforu tekstowego i wyświetla widok tekstu w oknie dokumentu o nazwie okna kodu. Dokument okna Kod jest zarządzany przez Menedżera okien kodu.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow>   
 [Dostarczanie kontekstu usługi języka za pomocą starszej wersji interfejsu API](../extensibility/providing-a-language-service-context-by-using-the-legacy-api.md)   
 [Funkcja IntelliSense hostingu](../extensibility/intellisense-hosting.md)   
 [Języki zawarte](../extensibility/contained-languages.md)   
 [Tworzenie starszej wersji usługi językowej](../extensibility/internals/developing-a-legacy-language-service.md)

