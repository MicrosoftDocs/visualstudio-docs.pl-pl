---
title: Okna narzędzi w rejestrze | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- tool windows, registering
ms.assetid: c4bb8add-7148-49e4-a377-01d059fd5524
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8cedb95ccd98c3d5bd5e05086cfd1b53b0f97cd9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68186385"
---
# <a name="tool-windows-in-the-registry"></a>Okna narzędzi w rejestrze
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pakietów VSPackage, które udostępniają okna narzędzi, muszą się zarejestrować w programie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] jako dostawcy okna narzędzi. Okna narzędzi utworzone za pomocą szablonu pakietu programu Visual Studio domyślnie wykonują tę czynność. Dostawcy okna narzędzi mają klucze rejestru systemowego, które określają atrybuty widoczności, takie jak domyślny rozmiar i lokalizację okna narzędzi, identyfikator GUID okna, który służy jako okienko narzędzia i układ dokowania.  
  
 Podczas opracowywania, dostawcy okna narzędzia zarządzanego rejestrują okna narzędzi, dodając atrybuty do kodu źródłowego, a następnie uruchamiając narzędzie RegPkg.exe w wyniku zestawu. Aby uzyskać więcej informacji, zobacz [Rejestrowanie okna narzędzi](../extensibility/registering-a-tool-window.md).  
  
## <a name="registering-unmanaged-tool-window-providers"></a>Rejestrowanie dostawców okien narzędzi niezarządzanych  
 Dostawcy okna narzędzi niezarządzanych muszą się zarejestrować [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] w sekcji ToolWindows rejestru systemowego. Poniższy fragment pliku reg przedstawia sposób rejestrowania okna narzędzia dynamicznego:  
  
```  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\<version number>\ToolWindows\{f0e1e9a1-9860-484d-ad5d-367d79aabf55}]  
@="{01069cdd-95ce-4620-ac21-ddff6c57f012}"  
"Name"="Microsoft.Samples.VisualStudio.IDE.ToolWindow.DynamicWindowPane"  
"Float"="250, 250, 410, 430"  
"DontForceCreate"=dword:00000001  
  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\ToolWindows\{f0e1e9a1-9860-484d-ad5d-367d79aabf55}\Visibility]  
"{f1536ef8-92ec-443c-9ed7-fdadf150da82}"=dword:00000000  
```  
  
 W pierwszym kluczu w powyższym przykładzie numer wersji to wersja programu, na przykład [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 7,1 lub 8,0, podklucz {f0e1e9a1-9860-484d-ad5d-367d79aabf55} jest identyfikatorem GUID okienka okna narzędzi (DynamicWindowPane), a wartość domyślna {01069cdd-95ce-4620-ac21-ddff6c57f012} jest identyfikatorem GUID pakietu VSPackage dostarczającym okno narzędzi. Aby uzyskać wyjaśnienie podkluczy zmiennoprzecinkowe i DontForceCreate, zobacz [Konfiguracja wyświetlania okna narzędzi](../extensibility/tool-window-display-configuration.md).  
  
 Drugi opcjonalny klucz, ToolWindows\Visibility, określa identyfikatory GUID poleceń, które wymagają, aby okno narzędzi było widoczne. W takim przypadku nie określono poleceń. Aby uzyskać więcej informacji, zobacz [Konfiguracja wyświetlania okna narzędzi](../extensibility/tool-window-display-configuration.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Pakietu VSPackage Essentials](../misc/vspackage-essentials.md)
