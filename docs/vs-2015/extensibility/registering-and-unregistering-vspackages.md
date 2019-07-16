---
title: Rejestrowanie i wyrejestrowywanie pakietów VSPackage | Dokumentacja firmy Microsoft
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
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68193817"
---
# <a name="registering-and-unregistering-vspackages"></a>Rejestrowanie i wyrejestrowywanie pakietów VSPackage
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Używanie atrybutów do zarejestrowania pakietu VSPackage, ale  
  
## <a name="registering-a-vspackage"></a>Rejestracja pakietu VSPackage  
 Atrybuty można użyć do kontrolowania rejestracji zarządzanego pakietów VSPackage. Wszystkie informacje o rejestracji znajduje się w pliku .pkgdef. Aby uzyskać więcej informacji na temat rejestracji opartych na plikach, zobacz [narzędzie CreatePkgDef](../extensibility/internals/createpkgdef-utility.md).  
  
 Poniższy kod przedstawia sposób używania atrybutów standardowa rejestracji można zarejestrować usługi pakietu VSPackage.  
  
```csharp  
[PackageRegistration(UseManagedResourcesOnly = true)]  
[Guid("0B81D86C-0A85-4f30-9B26-DD2616447F95")]  
public sealed class BasicPackage : Package  
{. . .}  
```  
  
## <a name="unregistering-an-extension"></a>Wyrejestrowywanie rozszerzenia  
 Jeśli zostały eksperymentowanie z dużą liczbą różnych pakietów VSPackage i chcesz je usunąć z doświadczalne wystąpienie, można po prostu uruchomisz **resetowania** polecenia. Wyszukaj **Zresetuj wystąpienie eksperymentalne programu Visual Studio** na stronie początkowej na komputerze lub uruchom następujące polecenie w wierszu polecenia:  
  
```vb  
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe" /Reset /VSInstance=14.0 /RootSuffix=Exp  
```  
  
 Jeśli chcesz odinstalować rozszerzenie, które zainstalowano na rozwój wystąpienia programu Visual Studio, przejdź do strony **narzędzia / rozszerzenia i aktualizacje**, znaleźć rozszerzenia, a kliknij **Odinstaluj**.  
  
 Jeśli jakiegoś powodu żadna z tych metod nie powiedzie się i wyznaczy odinstalować rozszerzenie, można wyrejestrować pakietu VSPackage zestawu z wiersza polecenia w następujący sposób:  
  
```  
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\regpkg” /unregister <pathToVSPackage assembly>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Pakiety VSPackage](../extensibility/internals/vspackages.md)
