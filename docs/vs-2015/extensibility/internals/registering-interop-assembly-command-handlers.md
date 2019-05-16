---
title: Rejestrowanie programów obsługi zestawu międzyoperacyjnego | Dokumentacja firmy Microsoft
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
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65705815"
---
# <a name="registering-interop-assembly-command-handlers"></a>Rejestrowanie programów obsługi zestawu międzyoperacyjnego
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Należy zarejestrować pakietu VSPackage [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] tak, aby prawidłowo polecenia kieruje zintegrowanego środowiska programistycznego (IDE).  
  
 Rejestru mogą być aktualizowane ręcznie edytując lub przy użyciu pliku rejestratora (.rgs). Aby uzyskać więcej informacji, zobacz [tworzenie skryptów rejestratora](https://msdn.microsoft.com/library/cbd5024b-8061-4a71-be65-7fee90374a35).  
  
 Framework pakietu zarządzanego (MPF) oferuje tę funkcję za pośrednictwem <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> klasy.  
  
 [Polecenie dokument referencyjny dotyczący formatowania tabeli](https://msdn.microsoft.com/09e9c6ef-9863-48de-9483-d45b7b7c798f) zasoby znajdują się w niezarządzanych satelitarnej biblioteki DLL interfejsu użytkownika.  
  
## <a name="command-handler-registration-of-a-vspackage"></a>Polecenie obsługi rejestracji pakietu VSPackage  
 Pakietu VSPackage działający jako procedura obsługi interfejsu użytkownika (UI)-na podstawie polecenia wymaga wpis rejestru o nazwie po pakietu VSPackage `GUID`. Ten wpis rejestru określa lokalizację pliku zasobów interfejsu użytkownika pakietu VSPackage i zasobu menu, w tym pliku. Wpis rejestru sam znajduje się w folderze HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\\*\<wersji >* \Menus, gdzie  *\<wersji >* jest wersją [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], na przykład 9.0.  
  
> [!NOTE]
> Ścieżka katalogu głównego HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*\<wersji >* może zostać zastąpiona przez alternatywne główne, kiedy [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] powłoki jest zainicjowany. Aby uzyskać więcej informacji o ścieżce katalogu głównego, zobacz [instalowanie pakietów VSPackage przy użyciu Instalatora Windows](../../extensibility/internals/installing-vspackages-with-windows-installer.md).  
  
### <a name="the-ctmenu-resource-registry-entry"></a>Wpis rejestru CTMENU zasobów  
 Struktura wpisu rejestru to:  
  
```  
HKEY_LOCAL_MACHINE\Software\VisualStudio\<Version>\  
  Menus\  
    <GUID> = <Resource Information>  
```  
  
 \<*Identyfikator GUID*> jest `GUID` z pakietu VSPackage w formie {XXXXXX-XXXX-XXXX-XXXX-XXXXXXXXX}.  
  
 *\<Informacje o zasobach >* składa się z trzech elementów oddzielonych przecinkami. Te elementy są w kolejności:  
  
 \<*Ścieżka do biblioteki DLL zasobu*>, \< *identyfikator zasobu Menu*>, \< *Menu wersji*>  
  
 W poniższej tabeli opisano pola \< *informacje o zasobach*>.  
  
|Element|Opis|  
|-------------|-----------------|  
|\<*Ścieżka do biblioteki DLL zasobu*>|Jest to pełna ścieżka do zasobu biblioteki DLL, która zawiera zasób menu lub to pole pozostanie puste, co oznacza, że zasób pakietu VSPackage DLL ma być używany (jak określono w podkluczu pakiety, w którym pakietu VSPackage, sama jest zarejestrowany).<br /><br /> Jest zwyczajowego można pozostawić to pole puste.|  
|\<*Identyfikator zasobu menu*>|To jest identyfikator zasobu `CTMENU` zasób, który zawiera wszystkie elementy interfejsu użytkownika dla pakietu VSPackage opracowanych z [vsct](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md) pliku.|  
|\<*Menu wersji*>|Jest to numer używany jako wersja dla `CTMENU` zasobów. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] używa tej wartości w celu określenia, czy wymagane remerge zawartość `CTMENU` zasób z pamięci podręcznej wszystkich `CTMENU` zasobów. Remerge jest wyzwalany przez wykonanie polecenia devenv Instalatora.<br /><br /> Ta wartość powinna początkowo ustawiona na 1 i zwiększany po każdej zmianie w `CTMENU` zasobów i przed wystąpieniem remerge.|  
  
### <a name="example"></a>Przykład  
 Oto przykład kilka wpisów zasobów:  
  
```  
HKEY_LOCAL_MACHINE\Software\VisualStudio\9.0Exp\  
  Menus\  
    {019971D6-4685-11D2-B48A-0000F87572EB} = ,1, 10  
    {1b027a40-8f43-11d0-8d11-00a0c91bc942} = , 10211, 3  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Jak dodać elementy interfejsu użytkownika w pakietach VSPackage](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Polecenia i menu, w których używane są zestawy międzyoperacyjne](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)
