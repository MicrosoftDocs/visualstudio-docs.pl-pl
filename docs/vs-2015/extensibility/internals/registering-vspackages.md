---
title: Rejestrowanie pakietów VSPackage | Dokumentacja firmy Microsoft
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
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68157389"
---
# <a name="registering-vspackages"></a>Rejestrowanie pakietów VSPackage
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] opiera się na plikach pkgdef do opisywania i zlokalizować pakietu VSPackage. Plik .pkgdef zawiera wszystkich informacji rejestracyjnych które w przeciwnym razie zostaną dodane do rejestru systemowego. Zarządzane pakietów VSPackage są rejestrowane przez dodawanie atrybutów do kodu źródłowego, a następnie uruchamiając [narzędzie CreatePkgDef](../../extensibility/internals/createpkgdef-utility.md) w zestawie wynikowym, aby wygenerować plik .pkgdef.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Określanie lokalizacji pliku pakietu VSPackage dla powłoki VS Shell](../../extensibility/internals/specifying-vspackage-file-location-to-the-vs-shell.md)  
 Opisuje ścieżkę ładowanie pakietów VSPackage.  
  
 [Rejestrowanie i wyrejestrowywanie pakietów VSPackage](../../extensibility/registering-and-unregistering-vspackages.md)  
 Wyjaśnia, jak zarejestrować pakietu VSPackage.  
  
 [Aby zarejestrować rozszerzenie za pomocą atrybutu niestandardowego rejestrowania](../../misc/using-a-custom-registration-attribute-to-register-an-extension.md)  
 W tym artykule opisano sposób tworzenia manifestu rejestracji, który może służyć do wdrażania zarządzanego pakietu VSPackage.
