---
title: Usługi języka oraz podstawowy edytor | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - language services
ms.assetid: e03199a6-ad5f-4075-bfba-8d36865112b7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9f3380545ce78defb57be8944881309ea2ab2990
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53929907"
---
# <a name="language-services-and-the-core-editor"></a>Usługi języka oraz podstawowy edytor
Edytory w programie Visual Studio są często skojarzone z usługą language. Między innymi usługi językowej zapewnia kolorowanie składni, uzupełniania instrukcji, funkcja IntelliSense i formatowania tekstu.  
  
## <a name="core-editors-and-document-data-objects"></a>Edytory podstawowe i obiekty danych dokumentu  
 Gdy uzyskujesz dostęp do edytora podstawowych, nie należy tworzyć dane dokumentu i obiektów widoku dokumentu. IDE tworzy i kontroluje te dwa obiekty i można uzyskać dojścia do nich, wprowadzając odpowiednie wywołania w edytorze fabryki implementacji.  
  
 Aby uzyskać więcej informacji, zobacz [ustalić, które edytora otwiera plik w projekcie](../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md).  
  
## <a name="language-services-and-the-core-editor"></a>Usługi języka oraz podstawowy edytor  
 Przez zaimplementowanie usługi językowej, można kontrolować sposób wyświetlania danych w widoku dokumentu. Usługa języka zawiera informacje i zachowanie, które są specyficzne dla danego języka, takich jak Visual C++. Podczas utworzyć buforu tekstu i określić rozszerzenie nazwy pliku dla dokumentu jest otwierana, buforu tekstowego określa skojarzony z tym rozszerzeniem nazwy pliku z klucza rejestru, usługa językowa **HKEY_LOCAL_MACHINE\SOFTWARE\ Microsoft\Editors\\\Extensions {identyfikator GUID YourLanguageService}**. Standardowa pakietu VSPackage, następnie ładowania procedury ładowania usługi pakietu VSPackage i tworzone jest wystąpienie usługi języka.  
  
 Usługa podstawowy język jest wyświetlany na poniższej ilustracji.  
  
 ![Grafika przedstawiająca usługi Model języka](../extensibility/media/vslanguageservicemodel.gif "vsLanguageServiceModel")  
Obiekty usługi podstawowej Edytor i język  
  
 Obiekt danych dokumentu na podstawowy edytor nosi nazwę bufor tekstowy i jest reprezentowana przez <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> obiektu. Obiekt widoku dokumentu nosi nazwę widoku tekstu i jest reprezentowana przez <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow> obiektu. Te dwa obiekty współpracują ze sobą za pośrednictwem usługi języka, aby zapewnić spójny widok podstawowy edytor. Informacje z buforu tekstowego i wyświetla widok tekstu w oknie dokumentu o nazwie okna kodu. Dokument okna Kod jest zarządzany przez Menedżera okien kodu.  
  
## <a name="see-also"></a>Zobacz także  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow>   
 [Zapewnianie kontekstu usługi języka przy użyciu starszej wersji interfejsu API](../extensibility/providing-a-language-service-context-by-using-the-legacy-api.md)   
 [Funkcja IntelliSense hostingu](../extensibility/intellisense-hosting.md)   
 [Języki zawarte](../extensibility/contained-languages.md)   
 [Tworzenie starszej wersji usługi językowej](../extensibility/internals/developing-a-legacy-language-service.md)