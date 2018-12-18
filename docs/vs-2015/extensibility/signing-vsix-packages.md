---
title: Podpisywanie pakietów VSIX | Dokumentacja firmy Microsoft
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
- signature
- signing
- authenticode
- vsix
- packages
ms.assetid: e34cfc2c-361c-44f8-9cfe-9f2be229d248
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 56ddcae38593d35bc8a31628bf3087dc79ca25c4
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51732548"
---
# <a name="signing-vsix-packages"></a>Podpisywanie pakietów VSIX
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zestawy rozszerzenia nie trzeba zostać podpisane przed uruchomieniem w programie Visual Studio, ale jest dobrym rozwiązaniem, aby to zrobić.  
  
 Jeśli chcesz zabezpieczyć swoje rozszerzenie i upewnij się, że nie została zmieniona z, można dodać podpis cyfrowy do pakietu VSIX. Po podpisaniu VSIX Instalator VSIX wyświetli komunikat wskazujący, że jest podpisany, a także dowiedzieć się więcej o samym podpisie. Jeśli zmodyfikowano zawartość pliku VSIX i VSIX nie została ponownie podpisana, Instalator VSIX będzie widoczne podpis jest nieprawidłowy. Instalacja nie zostanie zatrzymana, ale użytkownik jest wyświetlane ostrzeżenie.  
  
> [!IMPORTANT]
>  Począwszy od 2015 pakietów VSIX podpisany przy użyciu coś innego niż SHA256 szyfrowania zostaną zidentyfikowane jako posiadające nieprawidłowy podpis. Instalacji VSIX nie jest zablokowany, ale użytkownik będzie wyświetlane ostrzeżenie.  
  
## <a name="signing-a-vsix-with-vsixsigntool"></a>Podpisywanie za pomocą VSIXSignTool VSIX  
 Jest dostępne z narzędzia podpisywania szyfrowania SHA256 [VisualStudioExtensibility](http://www.nuget.org/profiles/VisualStudioExtensibility) w witrynie nuget.org na [VsixSignTool](http://www.nuget.org/packages/Microsoft.VSSDK.Vsixsigntool).  
  
#### <a name="to-use-the-vsixsigntool"></a>Aby użyć VSIXSignTool  
  
1. Dodawanie VSIX użytkownika do projektu.  
  
2. Kliknij prawym przyciskiem myszy węzeł projektu w Eksploratorze rozwiązań, wybierając **Dodaj &#124; Zarządzaj pakietami NuGet**.  Aby uzyskać więcej informacji na temat dodawania NuGet i NuGet Zobacz pakiety [Przegląd NuGet](http://docs.nuget.org/) i [Zarządzanie NuGet pakietów przy użyciu okna dialogowego](http://docs.nuget.org/Consume/Package-Manager-Dialog).  
  
3. Wyszukaj VSIXSignTool z VisualStudioExtensibility, a następnie zainstaluj pakiet NuGet.  
  
4. Możesz teraz uruchomić VSIXSignTool z lokalizacji lokalnej pakietów projektu. Poszukaj Pomoc wiersza polecenia narzędzia podpisywania scenariusza (VSIXSignTool.exe /?).  
  
   Na przykład aby zalogować się przy użyciu pliku certyfikatu chronione hasłem:  
  
   /F logowania VSIXSignTool.exe \<certfile > /p \<hasło > \<VSIXfile >  
  
## <a name="see-also"></a>Zobacz też  
 [Dostarczanie rozszerzeń programu Visual Studio](../extensibility/shipping-visual-studio-extensions.md)

