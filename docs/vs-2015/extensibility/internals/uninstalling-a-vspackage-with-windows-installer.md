---
title: Odinstalowywanie pakietów VSPackage przy użyciu Instalatora Windows | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- packages, uninstalling
- VSPackages, uninstalling
- uninstalling VSPackages
ms.assetid: c4575ac7-82da-4af8-a375-ea756a101fbf
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0082e86389620881c3879fe6dc79936b540d557f
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51742739"
---
# <a name="uninstalling-a-vspackage-with-windows-installer"></a>Odinstalowywanie pakietów VSPackage przy użyciu Instalatora Windows
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

W większości przypadków Instalatora Windows można odinstalować usługi pakietu VSPackage tylko przez "wycofanie" zastosowała do zainstalowania z pakietu VSPackage. Akcje niestandardowe omówione w [polecenia, musi być uruchamiania po instalacji](../../extensibility/internals/commands-that-must-be-run-after-installation.md) musi działać po odinstalowaniu także. Ponieważ wywołania devenv.exe występuje tuż przed działań standardowych InstallFinalize dla instalacji i dezinstalacji, wpisy tabeli Akcja niestandardowa i InstallExecuteSequence obsługiwać obu przypadkach.  
  
> [!NOTE]
>  Uruchom `devenv /setup` po odinstalowaniu pakietu MSI.  
  
 Zgodnie z ogólną zasadą po dodaniu akcji niestandardowych do pakietu Instalatora Windows można musi obsługiwać te akcje podczas dezinstalacji i wycofywania. Jeśli dodasz akcje niestandardowe, aby samodzielnie zarejestrować Twojego pakietu VSPackage, na przykład, należy dodać akcje niestandardowe, zbyt wyrejestrować.  
  
> [!NOTE]
>  Istnieje możliwość, użytkownik może zainstalować usługi pakietu VSPackage, a następnie odinstaluj wersje [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] za pomocą którego jest zintegrowany. Pomaga zagwarantować, że Dezinstalacja Twojego pakietu VSPackage działa w tym scenariuszu, eliminując akcje niestandardowe, korzystających z kodu za pomocą zależności [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
## <a name="handling-launch-conditions-at-uninstall-time"></a>Obsługa uruchamiania warunków na dezinstalacji.  
 Działania standardowe LaunchConditions odczytuje wiersze tabeli LaunchCondition, aby wyświetlić błąd komunikaty, jeśli warunki nie są spełnione. Jak warunków uruchamiania są zazwyczaj używane do zapewnienia, że spełnione są wymagania systemowe, możesz ogólnie pominąć warunków uruchamiania podczas odinstalowywania, dodając warunku, `NOT Installed`, aby wiersz LaunchConditions tabeli LaunchCondition.  
  
 Alternatywą jest dodanie `OR Installed` można uruchomić warunki, które nie są istotne podczas dezinstalacji. Zapewnia, że warunek jest zawsze wartość true, podczas odinstalowywania i w związku z tym nie wyświetli komunikat o błędzie w stanie uruchomienia.  
  
> [!NOTE]
>  `Installed` jest to właściwość, Instalator Windows zestawów po wykryciu, że Twoje pakietu VSPackage został już zainstalowany w systemie.  
  
## <a name="see-also"></a>Zobacz też  
 [Instalator Windows](http://msdn.microsoft.com/en-us/187d8965-c79d-4ecb-8689-10930fa8b3b5)   
 [Wykrywanie wymagań systemowych](../../extensibility/internals/detecting-system-requirements.md)

