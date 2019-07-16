---
title: Usługi języka oraz podstawowy edytor | Dokumentacja firmy Microsoft
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
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68180304"
---
# <a name="language-services-and-the-core-editor"></a>Usługi językowe oraz edytor podstawowy
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Edytory w programie Visual Studio są często skojarzone z usługą language. Między innymi usługi językowej zapewnia kolorowanie składni, uzupełniania instrukcji, funkcja IntelliSense i formatowania tekstu.  
  
## <a name="core-editors-and-document-data-objects"></a>Edytory podstawowe i obiekty danych dokumentu  
 Gdy uzyskujesz dostęp do edytora podstawowych, nie należy tworzyć dane dokumentu i obiektów widoku dokumentu. IDE tworzy i kontroluje te dwa obiekty i można uzyskać dojścia do nich, wprowadzając odpowiednie wywołania w edytorze fabryki implementacji.  
  
 Aby uzyskać więcej informacji, zobacz [określająca, które edytora otwiera plik w projekcie](../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md).  
  
## <a name="language-services-and-the-core-editor"></a>Usługi językowe oraz edytor podstawowy  
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
