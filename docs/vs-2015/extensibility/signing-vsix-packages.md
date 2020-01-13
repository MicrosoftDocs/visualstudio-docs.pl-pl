---
title: Podpisywanie pakietów VSIX | Microsoft Docs
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
ms.openlocfilehash: a4efaaa78ce593d8b97d1df454a9c30c2e62d9f8
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/13/2020
ms.locfileid: "75918736"
---
# <a name="signing-vsix-packages"></a>Podpisywanie pakietów VSIX
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zestawy rozszerzeń nie muszą być podpisane, zanim będą mogły działać w programie Visual Studio, ale jest to dobre rozwiązanie.  
  
 Jeśli chcesz zabezpieczyć rozszerzenie i upewnić się, że nie zostało ono naruszone, możesz dodać podpis cyfrowy do pakietu VSIX. Gdy VSIX jest podpisany, Instalator VSIX wyświetli komunikat informujący o tym, że jest podpisany, oraz więcej informacji o podpisie. Jeśli zawartość VSIX została zmodyfikowana, a VSIX nie został jeszcze podpisany, Instalator VSIX pokazuje, że sygnatura jest nieprawidłowa. Instalacja nie została zatrzymana, ale użytkownik jest ostrzegany.  
  
> [!IMPORTANT]
> Począwszy od 2015, pakiety VSIX podpisane przy użyciu elementów innych niż szyfrowanie SHA256 będą identyfikowane jako mające nieprawidłową sygnaturę. Instalacja VSIX nie jest blokowana, ale użytkownik zostanie poinformowany.  
  
## <a name="signing-a-vsix-with-vsixsigntool"></a>Podpisywanie VSIX przy użyciu VSIXSignTool  
 Istnieje narzędzie podpisywania SHA256 szyfrowania dostępne z [VisualStudioExtensibility](https://www.nuget.org/profiles/VisualStudioExtensibility) na NuGet.org na [VsixSignTool](https://www.nuget.org/packages/Microsoft.VSSDK.Vsixsigntool).  
  
#### <a name="to-use-the-vsixsigntool"></a>Aby użyć VSIXSignTool  
  
1. Dodaj swój VSIX do projektu.  
  
2. Kliknij prawym przyciskiem myszy węzeł projektu w Eksplorator rozwiązań, wybierając pozycję **Dodaj &#124; Zarządzaj pakietami NuGet**.  Aby uzyskać więcej informacji o pakiecie NuGet i dodawaniu pakietów NuGet, zobacz [Omówienie narzędzia NuGet](/nuget/) i [Zarządzanie pakietami NuGet przy użyciu okna dialogowego](/nuget/consume-packages/install-use-packages-visual-studio).  
  
3. Wyszukaj VSIXSignTool z VisualStudioExtensibility i zainstaluj pakiet NuGet.  
  
4. Teraz można uruchomić VSIXSignTool z lokalizacji lokalnych pakietów projektu. Zapoznaj się z pomocą narzędzia wiersza polecenia dla scenariusza podpisywania (VSIXSignTool. exe/?).  
  
   Na przykład, aby podpisać przy użyciu pliku certyfikatu chronionego hasłem:  
  
   VSIXSignTool. exe Podpisz/f \<CERTFILE >/p \<hasło > \<VSIXfile >  
  
## <a name="see-also"></a>Zobacz też  
 [Dostarczanie rozszerzeń programu Visual Studio](../extensibility/shipping-visual-studio-extensions.md)
