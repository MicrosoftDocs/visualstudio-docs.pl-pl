---
title: Rejestrowanie pakietów VSPackage | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- managed VSPackages, registering
- registration, managed VSPackages
ms.assetid: 79b9424e-7e9b-4fc8-9b9f-00212674573c
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 053157b0ce1cb4250d8c666725431515c75b5fa2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68157389"
---
# <a name="registering-vspackages"></a>Rejestrowanie pakietów VSPackage
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] opiera się na plikach. pkgdef do opisywania i lokalizowania pakietu VSPackage. Plik. pkgdef zawiera wszystkie informacje rejestracyjne, które w przeciwnym razie byłyby dodawane do rejestru systemowego. Zarządzane pakietów VSPackage są rejestrowane przez dodanie atrybutów do kodu źródłowego, a następnie uruchomienie [Narzędzia CreatePkgDef](../../extensibility/internals/createpkgdef-utility.md) na zestawie danych wyjściowych w celu wygenerowania pliku. pkgdef.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Określanie lokalizacji pliku pakietu VSPackage dla powłoki VS Shell](../../extensibility/internals/specifying-vspackage-file-location-to-the-vs-shell.md)  
 Opisuje ścieżkę ładowania dla pakietów VSPackage.  
  
 [Rejestrowanie i wyrejestrowywanie pakietów VSPackage](../../extensibility/registering-and-unregistering-vspackages.md)  
 Wyjaśnia, jak zarejestrować pakietu VSPackage.  
  
 [Używanie niestandardowego atrybutu rejestracji do rejestrowania rozszerzenia](../../misc/using-a-custom-registration-attribute-to-register-an-extension.md)  
 Opisuje sposób tworzenia manifestu rejestracji, którego można użyć do wdrożenia zarządzanego pakietu VSPackage.
