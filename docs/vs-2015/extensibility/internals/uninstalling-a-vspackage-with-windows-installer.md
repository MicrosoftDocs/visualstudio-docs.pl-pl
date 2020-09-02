---
title: Odinstalowywanie pakietu VSPackage z Instalator Windows | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- packages, uninstalling
- VSPackages, uninstalling
- uninstalling VSPackages
ms.assetid: c4575ac7-82da-4af8-a375-ea756a101fbf
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9a309779850dd33b77b426beb5627f61c40c2c4f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65675242"
---
# <a name="uninstalling-a-vspackage-with-windows-installer"></a>Odinstalowywanie pakietów VSPackage przy użyciu Instalatora Windows
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

W największej części Instalator Windows można odinstalować pakietu VSPackage tylko przez "wycofywanie" co miało na celu zainstalowanie pakietu VSPackage. Akcje niestandardowe omówione w [poleceniach, które muszą zostać uruchomione po instalacji](../../extensibility/internals/commands-that-must-be-run-after-installation.md) , muszą zostać uruchomione po odinstalowaniu programu. Ponieważ wywołania devenv.exe wystąpią tuż przed akcją standardu funkcję InstallFinalize zarówno w przypadku instalacji, jak i dezinstalacji, w obu przypadkach w tabeli.  
  
> [!NOTE]
> Uruchom `devenv /setup` po odinstalowaniu pakietu msi.  
  
 Zgodnie z ogólną regułą, jeśli dodajesz niestandardowe akcje do pakietu Instalator Windows, musisz obsługiwać te akcje podczas odinstalowywania i wycofywania. Jeśli dodasz niestandardowe akcje do samorejestruj pakietu VSPackage, na przykład musisz dodać niestandardowe akcje, aby je wyrejestrować.  
  
> [!NOTE]
> Użytkownik może zainstalować pakietu VSPackage, a następnie odinstalować wersje programu, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] z którymi jest ona zintegrowana. Możesz pomóc zapewnić, że Dezinstalacja pakietu VSPackage działa w tym scenariuszu, eliminując niestandardowe akcje, które uruchamiają kod z zależnościami od [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
## <a name="handling-launch-conditions-at-uninstall-time"></a>Obsługa warunków uruchamiania w czasie dezinstalacji  
 Akcja standard LaunchConditions odczytuje wiersze tabeli LaunchCondition w celu wyświetlenia komunikatów o błędach, jeśli warunki nie są spełnione. Ponieważ warunki uruchamiania są zwykle używane do zapewnienia, że wymagania systemowe są spełnione, można zwykle pominąć warunki uruchamiania podczas odinstalowywania, dodając warunek, `NOT Installed` do wiersza LaunchConditions tabeli LaunchCondition.  
  
 Alternatywą jest dodanie `OR Installed` do warunków uruchamiania, które nie są ważne podczas odinstalowywania. Dzięki temu warunek będzie zawsze prawdziwy podczas odinstalowywania i w związku z tym nie zostanie wyświetlony komunikat o błędzie stanu uruchomienia.  
  
> [!NOTE]
> `Installed` jest właściwością Instalator Windows ustawianą, gdy wykryje, że pakietu VSPackage został już zainstalowany w systemie.  
  
## <a name="see-also"></a>Zobacz też  
 [Instalator Windows](https://msdn.microsoft.com/187d8965-c79d-4ecb-8689-10930fa8b3b5)   
 [Wykrywanie wymagań systemowych](../../extensibility/internals/detecting-system-requirements.md)
