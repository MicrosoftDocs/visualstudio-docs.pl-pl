---
title: Rejestrowanie programów obsługi poleceń zestawu Interop | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- interop assemblies, command handlers
- command handling with interop assemblies, registering
ms.assetid: 303cd399-e29d-4ea1-8abe-5e0b59c12a0c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7e2ab6389f1e0d369dd095290d12c97431c44155
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705862"
---
# <a name="registering-interop-assembly-command-handlers"></a>Rejestrowanie programów obsługi zestawu międzyoperacyjnego
VsPackage musi zarejestrować się [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] w taki sposób, aby zintegrowane środowisko programistyczne (IDE) kieruje swoje polecenia poprawnie.

 Rejestr można aktualizować ręcznie, edytując lub używając pliku Rejestratora (.rgs). Aby uzyskać więcej informacji, zobacz [Tworzenie skryptów rejestratora](/cpp/atl/creating-registrar-scripts).

 Struktura pakietu zarządzanego (MPF) zapewnia <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> tę funkcjonalność za pośrednictwem klasy.

- Zasoby [referencyjne formatu tabeli poleceń](https://msdn.microsoft.com/library/09e9c6ef-9863-48de-9483-d45b7b7c798f) znajdują się w niezarządzanych dl interfejsu użytkownika satelitarnego.

## <a name="command-handler-registration-of-a-vspackage"></a>Rejestracja programu obsługi poleceń pakietu VSPackage
 VsPackage działający jako program obsługi dla poleceń opartych na interfejsie użytkownika (UI) wymaga wpisu rejestru nazwanego po programie VSPackage `GUID`. Ten wpis rejestru określa lokalizację pliku zasobów interfejsu użytkownika programu VSPackage i zasobu menu w tym pliku. Sam wpis rejestru znajduje się w obszarze HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\\*\<Version>* \Menus, gdzie * \<wersja>* jest wersją [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], na przykład 9.0.

> [!NOTE]
> Ścieżka główna HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*\<Version>* może zostać zastąpiona alternatywnym katalogiem głównym [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] po zainicjowaniu powłoki. Aby uzyskać więcej informacji na temat ścieżki głównej, zobacz [Instalowanie pakietów VSPackages z Instalatorem Windows](../../extensibility/internals/installing-vspackages-with-windows-installer.md).

### <a name="the-ctmenu-resource-registry-entry"></a>Wpis rejestru zasobów CTMENU
 Struktura wpisu rejestru jest:

```
HKEY_LOCAL_MACHINE\Software\VisualStudio\<Version>\
  Menus\
    <GUID> = <Resource Information>
```

 \<*GUID*> jest `GUID` vsPackage w postaci {XXXXXX-XXXX-XXXX-XXXX-XXXXXXXXX}.

 *Informacje o zasobie>składa się z trzech elementów oddzielonych przecinkami. \<* Elementy te są, w kolejności:

 \<*Ścieżka do biblioteki DLL zasobu*>, \<identyfikator *zasobu menu*>, \<wersja *menu*>

 W poniższej tabeli \<opisano pola *> informacji o zasobach.*

| Element | Opis |
|---------------------------| - |
| \<*Ścieżka do biblioteki DLL zasobu*> | Jest to pełna ścieżka do biblioteki DLL zasobu, która zawiera zasób menu lub jest ona pozostawiona pusta, co oznacza, że biblioteka DLL zasobu VSPackage ma być używana (jak określono w podkluczach Packages, w którym jest zarejestrowany sam plik VSPackage).<br /><br /> Zwyczajowo pozostawia to pole jest puste. |
| \<*Identyfikator zasobu menu*> | Jest to identyfikator zasobu, `CTMENU` który zawiera wszystkie elementy interfejsu użytkownika dla VSPackage skompilowany z pliku [vsct.](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md) |
| \<*Wersja menu*> | Jest to liczba używana jako `CTMENU` wersja zasobu. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]używa tej wartości, aby ustalić, czy musi ponownie `CTMENU` zamerge zawartości `CTMENU` zasobu z jego pamięci podręcznej wszystkich zasobów. Ponowne użycie jest wyzwalane przez wykonanie polecenia konfiguracji devenv.<br /><br /> Ta wartość powinna początkowo być ustawiona na 1 i `CTMENU` zwiększana po każdej zmianie w zasobie i przed wystąpieniem ponownego zasilić. |

### <a name="example"></a>Przykład
 Oto przykład kilku wpisów zasobów:

```
HKEY_LOCAL_MACHINE\Software\VisualStudio\9.0Exp\
  Menus\
    {019971D6-4685-11D2-B48A-0000F87572EB} = ,1, 10
    {1b027a40-8f43-11d0-8d11-00a0c91bc942} = , 10211, 3
```

## <a name="see-also"></a>Zobacz też
- [Dodawanie elementów interfejsu użytkownika przy użyciu pakietów VSPackage](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Polecenia i menu, w których używane są zestawy międzyoperacyjne](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)
