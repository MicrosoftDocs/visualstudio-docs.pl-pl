---
title: Rejestrowanie i Wyrejestrowywanie pakietów VSPackage | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- registration, VSPackages
- VSPackages, registering
ms.assetid: e25e7a46-6a55-4726-8def-ca316f553d6b
caps.latest.revision: 36
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1f6bc85fb00c15831dcf1a9f64e4b886272df218
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68193817"
---
# <a name="registering-and-unregistering-vspackages"></a>Rejestrowanie i wyrejestrowywanie pakietów VSPackage
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Używasz atrybutów do zarejestrowania pakietu VSPackage, ale  
  
## <a name="registering-a-vspackage"></a>Rejestrowanie elementu pakietu VSPackage  
 Za pomocą atrybutów można kontrolować rejestrację zarządzanych pakietów VSPackage. Wszystkie informacje o rejestracji są zawarte w pliku. pkgdef. Aby uzyskać więcej informacji na temat rejestracji na podstawie plików, zobacz [Narzędzie CreatePkgDef](../extensibility/internals/createpkgdef-utility.md).  
  
 Poniższy kod pokazuje, jak używać standardowych atrybutów rejestracji do rejestrowania pakietu VSPackage.  
  
```csharp  
[PackageRegistration(UseManagedResourcesOnly = true)]  
[Guid("0B81D86C-0A85-4f30-9B26-DD2616447F95")]  
public sealed class BasicPackage : Package  
{. . .}  
```  
  
## <a name="unregistering-an-extension"></a>Wyrejestrowywanie rozszerzenia  
 Jeśli eksperymentowanie zostało wykonane z dużą ilością pakietów VSPackage i chcesz je usunąć z wystąpienia eksperymentalnego, można po prostu uruchomić polecenie **Reset** . Wyszukaj pozycję **Zresetuj wystąpienie eksperymentalne programu Visual Studio** na stronie startowej komputera lub Uruchom to polecenie w wierszu polecenia:  
  
```vb  
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe" /Reset /VSInstance=14.0 /RootSuffix=Exp  
```  
  
 Jeśli chcesz odinstalować rozszerzenie, które zostało zainstalowane w wystąpieniu deweloperskim programu Visual Studio, przejdź do pozycji **Narzędzia/rozszerzenia i aktualizacje**, Znajdź rozszerzenie, a następnie kliknij przycisk **Odinstaluj**.  
  
 Jeśli z jakiegoś powodu żadna z tych metod nie powiedzie się po odinstalowaniu rozszerzenia, można wyrejestrować zestaw pakietu VSPackage z wiersza polecenia w następujący sposób:  
  
```  
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\regpkg” /unregister <pathToVSPackage assembly>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Pakiety VSPackage](../extensibility/internals/vspackages.md)
