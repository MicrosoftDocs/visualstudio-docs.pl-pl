---
title: Narzędzia Windows w rejestrze | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tool windows, registering
ms.assetid: c4bb8add-7148-49e4-a377-01d059fd5524
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: adb79fec233171a0d20e817f9675aaab8e7228f8
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56693168"
---
# <a name="tool-windows-in-the-registry"></a>Narzędzie Windows w rejestrze
Należy zarejestrować pakietów VSPackage, zapewniające okien narzędzi [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] jako narzędzie dostawców okna. Narzędzie okien utworzone za pomocą szablonu pakietu Visual Studio w tym domyślnie. Dostarczających okno narzędzia ma klucze rejestru systemu, które określają atrybuty widoczności, takie jak domyślny rozmiar okna narzędzia i lokalizację, identyfikator GUID okna, które służy jako okienko narzędzi i styl dokowania.

 Podczas tworzenia aplikacji dostarczających okna narzędzia zarządzanych zarejestrować okna narzędzi, dodawanie atrybutów do kodu źródłowego, a następnie uruchamiając narzędzie RegPkg.exe na wynikowy zestaw. Aby uzyskać więcej informacji, zobacz [rejestrowanie okna narzędzi](../extensibility/registering-a-tool-window.md).

## <a name="registering-unmanaged-tool-window-providers"></a>Rejestrowanie dostawców okna narzędzia niezarządzanych
 Należy zarejestrować dostawcy okna narzędzia niezarządzanych [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] w sekcji ToolWindows w rejestrze systemowym. Poniższy fragment pliku reg pokazuje, jak może zostać zarejestrowana dynamicznego okna narzędzi:

```
- [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\<version number>\ToolWindows\{f0e1e9a1-9860-484d-ad5d-367d79aabf55}]
@="{01069cdd-95ce-4620-ac21-ddff6c57f012}"
"Name"="Microsoft.Samples.VisualStudio.IDE.ToolWindow.DynamicWindowPane"
"Float"="250, 250, 410, 430"
"DontForceCreate"=dword:00000001

- [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\ToolWindows\{f0e1e9a1-9860-484d-ad5d-367d79aabf55}\Visibility]
"{f1536ef8-92ec-443c-9ed7-fdadf150da82}"=dword:00000000
```

 Pierwszy klucz w powyższym przykładzie, numer wersji to wersja [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], takie jak w wersji 7.1 lub 8.0, podklucz {f0e1e9a1-9860-484d-ad5d-367d79aabf55} jest identyfikatorem GUID okienka w oknie narzędzia (DynamicWindowPane), a {wartość domyślną 01069cdd-95ce-4620-ac21-ddff6c57f012} jest identyfikator GUID pakietu VSPackage, zapewniając okna narzędzia. Objaśnienia dotyczące podkluczy zmiennoprzecinkowych i DontForceCreate, zobacz [konfiguracji wyświetlania okna narzędzia](../extensibility/tool-window-display-configuration.md).

 Drugi klucz opcjonalne ToolWindows\Visibility, określa identyfikator GUID w faktycznej poleceń, które wymagają okna narzędzi, aby były widoczne. W tym przypadku nie istnieją żadne polecenia nie określono. Aby uzyskać więcej informacji, zobacz [konfiguracji wyświetlania okna narzędzia](../extensibility/tool-window-display-configuration.md).

## <a name="see-also"></a>Zobacz też
- [Pakiety VSPackage](../extensibility/internals/vspackages.md)