---
title: Podpisywanie pakietów VSIX | Dokumenty firmy Microsoft
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
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 17179c35496fc19322c5bb951f4d04bc28e5d7bc
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700086"
---
# <a name="signing-vsix-packages"></a>Podpisywanie pakietów VSIX
Zestawy rozszerzeń nie muszą być podpisane, zanim będą mogły działać w programie Visual Studio, ale jest to dobra praktyka, aby to zrobić.

 Jeśli chcesz zabezpieczyć rozszerzenie i upewnij się, że nie zostało naruszone, możesz dodać podpis cyfrowy do pakietu VSIX. Po podpisaniu vsix instalator VSIX wyświetli komunikat wskazujący, że jest podpisany, a także więcej informacji o samym podpisie. Jeśli zawartość VSIX zostały zmodyfikowane, a VSIX nie został podpisany ponownie, instalator VSIX pokaże, że podpis jest nieprawidłowy. Instalacja nie zostanie zatrzymana, ale użytkownik zostanie ostrzeżony.

> [!IMPORTANT]
> Począwszy od programu Visual Studio 2015 pakiety VSIX podpisane przy użyciu czegokolwiek innego niż szyfrowanie SHA256 zostaną zidentyfikowane jako posiadające nieprawidłowy podpis. Instalacja VSIX nie jest zablokowana, ale użytkownik zostanie ostrzeżony.

## <a name="signing-a-vsix-with-vsixsigntool"></a>Podpisywanie VSIX za pomocą VSIXSignTool
 W [visualstudioExtensibility](https://www.nuget.org/profiles/VisualStudioExtensibility) na nuget.org w [vsixSignTool](https://www.nuget.org/packages/Microsoft.VSSDK.Vsixsigntool)dostępne jest narzędzie do podpisywania szyfrowania SHA256.

#### <a name="to-use-the-vsixsigntool"></a>Aby użyć vsixsigntool

1. Dodaj vsix do projektu.

2. Kliknij prawym przyciskiem myszy węzeł projektu w Eksploratorze rozwiązań, wybierając pozycję **Dodaj &#124; Zarządzaj pakietami NuGet**.  Aby uzyskać więcej informacji na temat NuGet i dodawanie pakietów NuGet zobacz [nuget dokumentacji](/NuGet) i [menedżer pakietów tematów interfejsu użytkownika.](/NuGet/Tools/Package-Manager-UI)

3. Wyszukaj vsixsigntool z VisualStudioExtensibility i zainstalować pakiet NuGet.

4. Teraz można uruchomić VSIXSignTool z lokalizacji pakietów lokalnych projektu. Zapoznaj się z pomocą wiersza polecenia narzędzia dla scenariusza podpisywania (VSIXSignTool.exe /?).

   Na przykład, aby podpisać się za pomocą pliku certyfikatu chronionego hasłem:

   VsIXSignTool.exe sign \</f certfile> \</p password \<> VSIXfile>

## <a name="see-also"></a>Zobacz też
- [Dostarczanie rozszerzeń programu Visual Studio](../extensibility/shipping-visual-studio-extensions.md)
