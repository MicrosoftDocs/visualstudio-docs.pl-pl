---
title: Rejestrowanie programów obsługi poleceń zestawu międzyoperacyjnego | Microsoft Docs
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
ms.openlocfilehash: dfff8e4e6cc8ba3974ec70e6466b25e9ff7432e4
ms.sourcegitcommit: 4b29efeb3a5f05888422417c4ee236e07197fb94
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/11/2020
ms.locfileid: "90012051"
---
# <a name="registering-interop-assembly-command-handlers"></a>Rejestrowanie programów obsługi zestawu międzyoperacyjnego
Pakietu VSPackage musi się zarejestrować w programie, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Aby zintegrowane środowisko programistyczne (IDE) prawidłowo kieruje swoje polecenia.

 Rejestr można aktualizować przez ręczną edycję lub przy użyciu pliku rejestratora (. RGS). Aby uzyskać więcej informacji, zobacz [Tworzenie skryptów rejestratora](/cpp/atl/creating-registrar-scripts).

 Struktura pakietu zarządzanego (MPF) udostępnia tę funkcję za pomocą <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> klasy.

- Zasoby [referencyjne w formacie tabeli poleceń](/previous-versions/bb164647(v=vs.100)) znajdują się w niezarządzanych satelitach DLL interfejsu użytkownika.

## <a name="command-handler-registration-of-a-vspackage"></a>Rejestracja procedury obsługi poleceń pakietu VSPackage
 Pakietu VSPackage działający jako program obsługi poleceń opartych na interfejsie użytkownika wymaga wpisu rejestru o nazwie po pakietu VSPackage `GUID` . Ten wpis rejestru określa lokalizację pliku zasobów interfejsu użytkownika pakietu VSPackage i zasobu menu w tym pliku. Sam wpis rejestru znajduje się w obszarze HKEY_LOCAL_MACHINE \Software\Microsoft\VisualStudio \\ *\<Version>* \Menus, gdzie *\<Version>* jest wersją programu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , na przykład 9,0.

> [!NOTE]
> Ścieżka katalogu głównego HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\VisualStudio \\ *\<Version>* może zostać zastąpiona alternatywnym elementem głównym, gdy [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] powłoka zostanie zainicjowana. Aby uzyskać więcej informacji na temat ścieżki katalogu głównego, zobacz [Installing pakietów VSPackage With Instalator Windows](../../extensibility/internals/installing-vspackages-with-windows-installer.md).

### <a name="the-ctmenu-resource-registry-entry"></a>Wpis rejestru zasobów CTMENU
 Struktura wpisu rejestru to:

```
HKEY_LOCAL_MACHINE\Software\VisualStudio\<Version>\
  Menus\
    <GUID> = <Resource Information>
```

 \<*GUID*> jest `GUID` pakietu VSPackage w postaci {XXXXXX-xxxx-xxxx-xxxx-xxxxxxxxx}.

 *\<Resource Information>* składa się z trzech elementów oddzielonych przecinkami. Te elementy są w kolejności:

 \<*Path to Resource DLL*>, \<*Menu Resource ID*>, \<*Menu Version*>

 W poniższej tabeli opisano pola \<*Resource Information*> .

| Element | Opis |
|---------------------------| - |
| \<*Path to Resource DLL*> | Jest to pełna ścieżka do biblioteki DLL zasobu, która zawiera zasób menu lub to pole pozostanie puste, co oznacza, że biblioteka DLL zasobów pakietu VSPackage ma być używana (jak określono w podkluczu Packages, w którym jest zarejestrowana sama pakietu VSPackage).<br /><br /> Jest to niestandardowa wartość pola pozostaw puste. |
| \<*Menu Resource ID*> | Jest to identyfikator zasobu `CTMENU` zawierający wszystkie elementy interfejsu użytkownika dla pakietu VSPackage jako skompilowane z pliku [vsct](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md) . |
| \<*Menu Version*> | Jest to numer używany jako wersja dla `CTMENU` zasobu. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] używa tej wartości, aby określić, czy należy ponownie scalić zawartość `CTMENU` zasobu z jego pamięcią podręczną wszystkich `CTMENU` zasobów. Scalanie jest wyzwalane przez wykonanie polecenia Instalatora devenv.<br /><br /> Ta wartość powinna początkowo być ustawiona na 1 i zwiększona po każdej zmianie `CTMENU` zasobu i przed ponownym scaleniem. |

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