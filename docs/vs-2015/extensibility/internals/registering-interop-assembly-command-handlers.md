---
title: Rejestrowanie programów obsługi poleceń zestawu międzyoperacyjnego | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- interop assemblies, command handlers
- command handling with interop assemblies, registering
ms.assetid: 303cd399-e29d-4ea1-8abe-5e0b59c12a0c
caps.latest.revision: 20
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9d2822e9eef36806f5c251813925fb4244242519
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65705815"
---
# <a name="registering-interop-assembly-command-handlers"></a>Rejestrowanie programów obsługi zestawu międzyoperacyjnego
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Pakietu VSPackage musi się zarejestrować w programie, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Aby zintegrowane środowisko programistyczne (IDE) prawidłowo kieruje swoje polecenia.  
  
 Rejestr można aktualizować przez ręczną edycję lub przy użyciu pliku rejestratora (. RGS). Aby uzyskać więcej informacji, zobacz [Tworzenie skryptów rejestratora](https://msdn.microsoft.com/library/cbd5024b-8061-4a71-be65-7fee90374a35).  
  
 Struktura pakietu zarządzanego (MPF) udostępnia tę funkcję za pomocą <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> klasy.  
  
 Zasoby [referencyjne w formacie tabeli poleceń](https://msdn.microsoft.com/09e9c6ef-9863-48de-9483-d45b7b7c798f) znajdują się w niezarządzanych satelitach DLL interfejsu użytkownika.  
  
## <a name="command-handler-registration-of-a-vspackage"></a>Rejestracja procedury obsługi poleceń pakietu VSPackage  
 Pakietu VSPackage działający jako program obsługi poleceń opartych na interfejsie użytkownika wymaga wpisu rejestru o nazwie po pakietu VSPackage `GUID` . Ten wpis rejestru określa lokalizację pliku zasobów interfejsu użytkownika pakietu VSPackage i zasobu menu w tym pliku. Sam wpis rejestru znajduje się w obszarze HKEY_LOCAL_MACHINE \Software\Microsoft\VisualStudio \\ *\<Version>* \Menus, gdzie *\<Version>* jest wersją programu [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , na przykład 9,0.  
  
> [!NOTE]
> Ścieżka katalogu głównego HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\VisualStudio \\ *\<Version>* może zostać zastąpiona alternatywnym elementem głównym, gdy [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] powłoka zostanie zainicjowana. Aby uzyskać więcej informacji na temat ścieżki katalogu głównego, zobacz [Installing pakietów VSPackage With Instalator Windows](../../extensibility/internals/installing-vspackages-with-windows-installer.md).  
  
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
  
|Element|Opis|  
|-------------|-----------------|  
|\<*Path to Resource DLL*>|Jest to pełna ścieżka do biblioteki DLL zasobu, która zawiera zasób menu lub to pole pozostanie puste, co oznacza, że biblioteka DLL zasobów pakietu VSPackage ma być używana (jak określono w podkluczu Packages, w którym jest zarejestrowana sama pakietu VSPackage).<br /><br /> Jest to niestandardowa wartość pola pozostaw puste.|  
|\<*Menu Resource ID*>|Jest to identyfikator zasobu `CTMENU` zawierający wszystkie elementy interfejsu użytkownika dla pakietu VSPackage jako skompilowane z pliku [vsct](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md) .|  
|\<*Menu Version*>|Jest to numer używany jako wersja dla `CTMENU` zasobu. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] używa tej wartości, aby określić, czy należy ponownie scalić zawartość `CTMENU` zasobu z jego pamięcią podręczną wszystkich `CTMENU` zasobów. Scalanie jest wyzwalane przez wykonanie polecenia Instalatora devenv.<br /><br /> Ta wartość powinna początkowo być ustawiona na 1 i zwiększona po każdej zmianie `CTMENU` zasobu i przed ponownym scaleniem.|  
  
### <a name="example"></a>Przykład  
 Oto przykład kilku wpisów zasobów:  
  
```  
HKEY_LOCAL_MACHINE\Software\VisualStudio\9.0Exp\  
  Menus\  
    {019971D6-4685-11D2-B48A-0000F87572EB} = ,1, 10  
    {1b027a40-8f43-11d0-8d11-00a0c91bc942} = , 10211, 3  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Jak pakietów VSPackage Dodawanie elementów interfejsu użytkownika](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Polecenia i menu, w których używane są zestawy międzyoperacyjne](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)
