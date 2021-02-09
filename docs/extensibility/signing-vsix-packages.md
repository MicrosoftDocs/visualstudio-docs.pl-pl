---
title: Podpisywanie pakietów VSIX | Microsoft Docs
description: Dowiedz się więcej o zestawach rozszerzeń podpisywania. Instalator VSIX wyświetla komunikat informujący o tym, że VSIX jest podpisany i informacje o podpisie.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- signature
- signing
- authenticode
- vsix
- packages
ms.assetid: e34cfc2c-361c-44f8-9cfe-9f2be229d248
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a0127b16438191a7d4f10ebf351b697455f72b16
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99928032"
---
# <a name="signing-vsix-packages"></a>Podpisywanie pakietów VSIX
Zestawy rozszerzeń nie muszą być podpisane, zanim będą mogły działać w programie Visual Studio, ale jest to dobre rozwiązanie.

 Jeśli chcesz zabezpieczyć rozszerzenie i upewnić się, że nie zostało ono naruszone, możesz dodać podpis cyfrowy do pakietu VSIX. Gdy VSIX jest podpisany, Instalator VSIX wyświetli komunikat informujący o tym, że jest podpisany, oraz więcej informacji o podpisie. Jeśli zawartość VSIX została zmodyfikowana, a VSIX nie został jeszcze podpisany, Instalator VSIX pokazuje, że sygnatura jest nieprawidłowa. Instalacja nie została zatrzymana, ale użytkownik jest ostrzegany.

> [!IMPORTANT]
> Począwszy od programu Visual Studio 2015, pakiety VSIX podpisane przy użyciu innych elementów niż szyfrowanie SHA256 będą identyfikowane jako mające nieprawidłową sygnaturę. Instalacja VSIX nie jest blokowana, ale użytkownik zostanie poinformowany.

## <a name="signing-a-vsix-with-vsixsigntool"></a>Podpisywanie VSIX przy użyciu VSIXSignTool
 Istnieje narzędzie podpisywania SHA256 szyfrowania dostępne z [VisualStudioExtensibility](https://www.nuget.org/profiles/VisualStudioExtensibility) na NuGet.org na [VsixSignTool](https://www.nuget.org/packages/Microsoft.VSSDK.Vsixsigntool).

#### <a name="to-use-the-vsixsigntool"></a>Aby użyć VSIXSignTool

1. Dodaj swój VSIX do projektu.

2. Kliknij prawym przyciskiem myszy węzeł projektu w Eksplorator rozwiązań, a następnie wybierz pozycję **dodaj &#124; Zarządzaj pakietami NuGet**.  Aby uzyskać więcej informacji o pakiecie NuGet i dodawaniu pakietów NuGet, zobacz [dokumentację programu NuGet](/NuGet) i tematy dotyczące [interfejsu użytkownika Menedżera pakietów](/NuGet/Tools/Package-Manager-UI) .

3. Wyszukaj VSIXSignTool z VisualStudioExtensibility i zainstaluj pakiet NuGet.

4. Teraz można uruchomić VSIXSignTool z lokalizacji lokalnych pakietów projektu. Zapoznaj się z pomocą narzędzia wiersza polecenia dla scenariusza podpisywania (VSIXSignTool.exe/?).

   Na przykład, aby podpisać przy użyciu pliku certyfikatu chronionego hasłem:

   VSIXSignTool.exe podpisywanie/f \<certfile> /p \<password>\<VSIXfile>

## <a name="see-also"></a>Zobacz też
- [Dostarczanie rozszerzeń programu Visual Studio](../extensibility/shipping-visual-studio-extensions.md)
