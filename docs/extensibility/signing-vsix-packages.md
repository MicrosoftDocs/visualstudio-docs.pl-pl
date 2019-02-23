---
title: Podpisywanie pakietów VSIX | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- signature
- signing
- authenticode
- vsix
- packages
ms.assetid: e34cfc2c-361c-44f8-9cfe-9f2be229d248
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 952195ab33b9a7e35265f5ecf40a8de3cf958fb3
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56720591"
---
# <a name="signing-vsix-packages"></a>Podpisywanie pakietów VSIX
Zestawy rozszerzenia nie trzeba zostać podpisane przed uruchomieniem w programie Visual Studio, ale jest dobrym rozwiązaniem, aby to zrobić.

 Jeśli chcesz zabezpieczyć swoje rozszerzenie i upewnij się, że nie została zmieniona z, można dodać podpis cyfrowy do pakietu VSIX. Po podpisaniu VSIX Instalator VSIX wyświetli komunikat wskazujący, że jest podpisany, a także dowiedzieć się więcej o samym podpisie. Jeśli zmodyfikowano zawartość pliku VSIX i VSIX nie została ponownie podpisana, Instalator VSIX będzie widoczne podpis jest nieprawidłowy. Instalacja nie zostanie zatrzymana, ale użytkownik jest wyświetlane ostrzeżenie.

> [!IMPORTANT]
>  Począwszy od programu Visual Studio 2015, pakietów VSIX podpisany przy użyciu coś innego niż SHA256 szyfrowania zostaną zidentyfikowane jako posiadające nieprawidłowy podpis. Instalacji VSIX nie jest zablokowany, ale użytkownik będzie wyświetlane ostrzeżenie.

## <a name="signing-a-vsix-with-vsixsigntool"></a>Podpisywanie za pomocą VSIXSignTool VSIX
 Jest dostępne z narzędzia podpisywania szyfrowania SHA256 [VisualStudioExtensibility](http://www.nuget.org/profiles/VisualStudioExtensibility) w witrynie nuget.org na [VsixSignTool](http://www.nuget.org/packages/Microsoft.VSSDK.Vsixsigntool).

#### <a name="to-use-the-vsixsigntool"></a>Aby użyć VSIXSignTool

1. Dodawanie VSIX użytkownika do projektu.

2. Kliknij prawym przyciskiem myszy węzeł projektu w Eksploratorze rozwiązań, wybierając **Dodaj &#124; Zarządzaj pakietami NuGet**.  Aby uzyskać więcej informacji na temat dodawania NuGet i NuGet Zobacz pakiety [dokumentacja programu NuGet](/NuGet) i [interfejs użytkownika Menedżera pakietów](/NuGet/Tools/Package-Manager-UI) tematów.

3. Wyszukaj VSIXSignTool z VisualStudioExtensibility, a następnie zainstaluj pakiet NuGet.

4. Możesz teraz uruchomić VSIXSignTool z lokalizacji lokalnej pakietów projektu. Poszukaj Pomoc wiersza polecenia narzędzia podpisywania scenariusza (VSIXSignTool.exe /?).

   Na przykład aby zalogować się przy użyciu pliku certyfikatu chronione hasłem:

   VSIXSignTool.exe sign /f \<certfile> /p \<password> \<VSIXfile>

## <a name="see-also"></a>Zobacz też
- [Dostarczanie rozszerzeń programu Visual Studio](../extensibility/shipping-visual-studio-extensions.md)
