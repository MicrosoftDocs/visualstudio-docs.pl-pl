---
title: Narzędzia Windows w rejestrze | Dokumentacja firmy Microsoft
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
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68186385"
---
# <a name="tool-windows-in-the-registry"></a>Okna narzędzi w rejestrze
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Należy zarejestrować pakietów VSPackage, zapewniające okien narzędzi [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] jako narzędzie dostawców okna. Narzędzie okien utworzone za pomocą szablonu pakietu Visual Studio w tym domyślnie. Dostarczających okno narzędzia ma klucze rejestru systemu, które określają atrybuty widoczności, takie jak domyślny rozmiar okna narzędzia i lokalizację, identyfikator GUID okna, które służy jako okienko narzędzi i styl dokowania.  
  
 Podczas tworzenia aplikacji dostarczających okna narzędzia zarządzanych zarejestrować okna narzędzi, dodawanie atrybutów do kodu źródłowego, a następnie uruchamiając narzędzie RegPkg.exe na wynikowy zestaw. Aby uzyskać więcej informacji, zobacz [rejestrowanie okna narzędzi](../extensibility/registering-a-tool-window.md).  
  
## <a name="registering-unmanaged-tool-window-providers"></a>Rejestrowanie dostawców okna narzędzia niezarządzanych  
 Należy zarejestrować dostawcy okna narzędzia niezarządzanych [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] w sekcji ToolWindows w rejestrze systemowym. Poniższy fragment pliku reg pokazuje, jak może zostać zarejestrowana dynamicznego okna narzędzi:  
  
```  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\<version number>\ToolWindows\{f0e1e9a1-9860-484d-ad5d-367d79aabf55}]  
@="{01069cdd-95ce-4620-ac21-ddff6c57f012}"  
"Name"="Microsoft.Samples.VisualStudio.IDE.ToolWindow.DynamicWindowPane"  
"Float"="250, 250, 410, 430"  
"DontForceCreate"=dword:00000001  
  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\ToolWindows\{f0e1e9a1-9860-484d-ad5d-367d79aabf55}\Visibility]  
"{f1536ef8-92ec-443c-9ed7-fdadf150da82}"=dword:00000000  
```  
  
 Pierwszy klucz w powyższym przykładzie, numer wersji to wersja [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], takie jak w wersji 7.1 lub 8.0, podklucz {f0e1e9a1-9860-484d-ad5d-367d79aabf55} jest identyfikatorem GUID okienka w oknie narzędzia (DynamicWindowPane), a {wartość domyślną 01069cdd-95ce-4620-ac21-ddff6c57f012} jest identyfikator GUID pakietu VSPackage, zapewniając okna narzędzia. Objaśnienia dotyczące podkluczy zmiennoprzecinkowych i DontForceCreate, zobacz [konfiguracji wyświetlania okna narzędzia](../extensibility/tool-window-display-configuration.md).  
  
 Drugi klucz opcjonalne ToolWindows\Visibility, określa identyfikator GUID w faktycznej poleceń, które wymagają okna narzędzi, aby były widoczne. W tym przypadku nie istnieją żadne polecenia nie określono. Aby uzyskać więcej informacji, zobacz [konfiguracji wyświetlania okna narzędzia](../extensibility/tool-window-display-configuration.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Podstawowe informacje dotyczące pakietu VSPackage](../misc/vspackage-essentials.md)
