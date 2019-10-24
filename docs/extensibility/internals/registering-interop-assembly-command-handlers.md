---
title: Rejestrowanie programów obsługi poleceń zestawu międzyoperacyjnego | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- interop assemblies, command handlers
- command handling with interop assemblies, registering
ms.assetid: 303cd399-e29d-4ea1-8abe-5e0b59c12a0c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cbc0d162a11df034bec4d1f357ef8abd106da401
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72724688"
---
# <a name="registering-interop-assembly-command-handlers"></a>Rejestrowanie programów obsługi zestawu międzyoperacyjnego
Pakietu VSPackage musi zarejestrować się w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], aby zintegrowane środowisko programistyczne (IDE) prawidłowo kieruje swoje polecenia.

 Rejestr można aktualizować przez ręczną edycję lub przy użyciu pliku rejestratora (. RGS). Aby uzyskać więcej informacji, zobacz [Tworzenie skryptów rejestratora](/cpp/atl/creating-registrar-scripts).

 Struktura pakietu zarządzanego (MPF) udostępnia tę funkcję za pomocą klasy <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute>.

- Zasoby [referencyjne w formacie tabeli poleceń](https://msdn.microsoft.com/library/09e9c6ef-9863-48de-9483-d45b7b7c798f) znajdują się w niezarządzanych satelitach DLL interfejsu użytkownika.

## <a name="command-handler-registration-of-a-vspackage"></a>Rejestracja procedury obsługi poleceń pakietu VSPackage
 Pakietu VSPackage działający jako program obsługi poleceń opartych na interfejsie użytkownika wymaga wpisu rejestru o nazwie po pakietu VSPackage `GUID`. Ten wpis rejestru określa lokalizację pliku zasobów interfejsu użytkownika pakietu VSPackage i zasobu menu w tym pliku. Wpis rejestru znajduje się w obszarze HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio \\ *\<Version >* \Menus, gdzie *\<Version >* to wersja [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], na przykład 9,0.

> [!NOTE]
> Ścieżka katalogu głównego HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio \\ *\<Version >* może zostać zastąpiona alternatywnym katalogiem głównym po zainicjowaniu powłoki [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Aby uzyskać więcej informacji na temat ścieżki katalogu głównego, zobacz [Installing pakietów VSPackage With Instalator Windows](../../extensibility/internals/installing-vspackages-with-windows-installer.md).

### <a name="the-ctmenu-resource-registry-entry"></a>Wpis rejestru zasobów CTMENU
 Struktura wpisu rejestru to:

```
HKEY_LOCAL_MACHINE\Software\VisualStudio\<Version>\
  Menus\
    <GUID> = <Resource Information>
```

 \<*Identyfikator GUID*> jest `GUID` pakietu VSPackage w postaci {XXXXXX-XXXX-XXXX-XXXX-xxxxxxxxx}.

 *\<Resource informacje >* składa się z trzech elementów oddzielonych przecinkami. Te elementy są w kolejności:

 \<*ścieżka do biblioteki DLL zasobów*>, \<*identyfikator zasobu menu*>, \<*wersja menu* >

 W poniższej tabeli opisano pola \<*informacji o zasobach*>.

| Element | Opis |
|---------------------------| - |
| \<*ścieżkę do biblioteki DLL zasobów* > | Jest to pełna ścieżka do biblioteki DLL zasobu, która zawiera zasób menu lub to pole pozostanie puste, co oznacza, że biblioteka DLL zasobów pakietu VSPackage ma być używana (jak określono w podkluczu Packages, w którym jest zarejestrowana sama pakietu VSPackage).<br /><br /> Jest to niestandardowa wartość pola pozostaw puste. |
| *Identyfikator zasobu Menu* \< > | Jest to identyfikator zasobu `CTMENU`, który zawiera wszystkie elementy interfejsu użytkownika dla pakietu VSPackage jako skompilowane z pliku [vsct](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md) . |
| *wersja Menu* \< > | Jest to numer używany jako wersja `CTMENU`go zasobu. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] używa tej wartości, aby określić, czy należy ponownie scalić zawartość zasobu `CTMENU` z jego pamięcią podręczną wszystkich zasobów `CTMENU`. Scalanie jest wyzwalane przez wykonanie polecenia Instalatora devenv.<br /><br /> Ta wartość powinna początkowo być ustawiona na 1 i zwiększona po każdej zmianie w zasobie `CTMENU` i przed ponownym scaleniem. |

### <a name="example"></a>Przykład
 Oto przykład kilku wpisów zasobów:

```
HKEY_LOCAL_MACHINE\Software\VisualStudio\9.0Exp\
  Menus\
    {019971D6-4685-11D2-B48A-0000F87572EB} = ,1, 10
    {1b027a40-8f43-11d0-8d11-00a0c91bc942} = , 10211, 3
```

## <a name="see-also"></a>Zobacz także
- [Dodawanie elementów interfejsu użytkownika przy użyciu pakietów VSPackage](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Polecenia i menu, w których używane są zestawy międzyoperacyjne](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)