---
title: Podpisywanie pakietów VSIX | Microsoft Docs
description: Dowiedz się więcej o podpisywaniu zestawów rozszerzeń. Instalator VSIX wyświetla komunikat informujący o podpisie VSIX oraz informacje o samym podpisie.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- signature
- signing
- authenticode
- vsix
- packages
ms.assetid: e34cfc2c-361c-44f8-9cfe-9f2be229d248
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d481c75754c7bc49369987d4bf6dc3aa33e96fdc
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899163"
---
# <a name="signing-vsix-packages"></a>Podpisywanie pakietów VSIX
Zestawy rozszerzeń nie muszą być podpisane przed uruchomieniem w Visual Studio, ale jest to dobrym rozwiązaniem.

 Jeśli chcesz zabezpieczyć rozszerzenie i upewnić się, że nie zostało naruszone, możesz dodać podpis cyfrowy do pakietu VSIX. Po podpisaniu VSIX instalator VSIX wyświetli komunikat informujący o podpisie oraz więcej informacji o samym podpisie. Jeśli zawartość pliku VSIX została zmodyfikowana, a plik VSIX nie został podpisany ponownie, instalator VSIX pokaże, że podpis jest nieprawidłowy. Instalacja nie zostanie zatrzymana, ale użytkownik zostanie o tym ostrzec.

> [!IMPORTANT]
> Począwszy od Visual Studio 2015 r., pakiety VSIX podpisane przy użyciu czegokolwiek innego niż szyfrowanie SHA256 będą identyfikowane jako mające nieprawidłowy podpis. Instalacja VSIX nie jest blokowana, ale użytkownik zostanie o tym ostrzec.

## <a name="signing-a-vsix-with-vsixsigntool"></a>Podpisywanie VSIX za pomocą narzędzia VSIXSignTool
 Narzędzie podpisywania szyfrowania SHA256 jest dostępne w programie [VisualStudioExtensibility](https://www.nuget.org/profiles/VisualStudioExtensibility) nuget.org w [narzędziu VsixSignTool.](https://www.nuget.org/packages/Microsoft.VSSDK.Vsixsigntool)

#### <a name="to-use-the-vsixsigntool"></a>Aby użyć narzędzia VSIXSignTool

1. Dodaj vsix do projektu.

2. Kliknij prawym przyciskiem myszy węzeł projektu w Eksplorator rozwiązań, wybierając pozycję Dodaj &#124; **zarządzaj pakietami NuGet.**  Aby uzyskać więcej informacji na temat pakietów NuGet i dodawania pakietów NuGet, zobacz [dokumentację](/NuGet) i Menedżer pakietów [interfejsu](/NuGet/Tools/Package-Manager-UI) użytkownika.

3. Wyszukaj narzędzie VSIXSignTool w programie VisualStudioExtensibility i zainstaluj pakiet NuGet.

4. Teraz możesz uruchomić narzędzie VSIXSignTool z lokalizacji pakietów lokalnych projektu. Zapoznaj się z pomocą wiersza polecenia narzędzia dla scenariusza podpisywania (VSIXSignTool.exe /?).

   Aby na przykład zalogować się przy użyciu pliku certyfikatu chronionego hasłem:

   VSIXSignTool.exe /f \<certfile> /p \<password>\<VSIXfile>

## <a name="see-also"></a>Zobacz też
- [Dostarczanie rozszerzeń programu Visual Studio](../extensibility/shipping-visual-studio-extensions.md)
