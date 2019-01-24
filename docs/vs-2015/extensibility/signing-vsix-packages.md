---
title: Podpisywanie pakietów VSIX | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- signature
- signing
- authenticode
- vsix
- packages
ms.assetid: e34cfc2c-361c-44f8-9cfe-9f2be229d248
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c27b000748fdac99b78f0e7d0ff737356956a78d
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54776675"
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
  
   VSIXSignTool.exe sign /f \<certfile> /p \<password> \<VSIXfile>  
  
## <a name="see-also"></a>Zobacz też  
 [Dostarczanie rozszerzeń programu Visual Studio](../extensibility/shipping-visual-studio-extensions.md)
