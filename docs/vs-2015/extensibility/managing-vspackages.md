---
title: Zarządzanie pakietów VSPackage | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, autoloading
- VSPackages, delayed loading
- delay loading
- VSPackages, loading
ms.assetid: 386e0ce5-4107-4164-b0cd-1cf43eb5e7cf
caps.latest.revision: 36
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0b56ab490342cfbda9c16408aa0937abd80728c9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68194373"
---
# <a name="managing-vspackages"></a>Zarządzanie pakietami VSPackage
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W większości przypadków nie trzeba martwić się o zarządzanie pakietów VSPackage, ponieważ szablony projektów i elementów rejestrują i ładują pakiet automatycznie. Jednak w niektórych sytuacjach może być konieczne poznanie nieco więcej informacji w celu zarządzania pakietem.  
  
## <a name="using-the-experimental-instance"></a>Korzystanie z eksperymentalnego wystąpienia  
 Aby dowiedzieć się więcej o eksperymentalnym wystąpieniu, zobacz [wystąpienie eksperymentalne](../extensibility/the-experimental-instance.md).  
  
## <a name="registering-and-unregistering-vspackages"></a>Rejestrowanie i wyrejestrowywanie pakietów VSPackage  
 Aby dowiedzieć się, jak zarejestrować i wyrejestrować pakietów VSPackage i inne typy rozszerzeń, zobacz [Rejestrowanie i Wyrejestrowywanie pakietów VSPackage](../extensibility/registering-and-unregistering-vspackages.md).  
  
## <a name="loading-a-vspackage"></a>Ładowanie elementu pakietu VSPackage  
 Pakietów VSPackage można ustawić na automatyczne ładowanie, gdy określony identyfikator GUID CMDUICONTEXT jest włączony. Aby uzyskać więcej informacji, zobacz [ładowanie pakietów VSPackage](../extensibility/loading-vspackages.md).  
  
## <a name="using-asyncpackage-to-load-vspackages-in-the-background"></a>Ładowanie pakietów VSPackage w tle za pomocą AsyncPackage  
 Klasa AsyncPackage umożliwia ładowanie pakietów w wątku w tle w celu uzyskania lepszej czas odpowiedzi interfejsu użytkownika w programie Visual Studio. Aby uzyskać więcej informacji, zobacz [How to: use AsyncPackage to load pakietów VSPackage w tle](../extensibility/how-to-use-asyncpackage-to-load-vspackages-in-the-background.md).  
  
## <a name="rule-based-ui-context-for-extensions"></a>Kontekst interfejsu użytkownika oparty na regułach dla rozszerzeń  
 Konteksty interfejsu użytkownika oparte na regułach umożliwiają autorom rozszerzeń Definiowanie precyzyjnych warunków, w których kontekst interfejsu użytkownika jest aktywowany i załadowanych skojarzonych pakietów VSPackage. Aby uzyskać więcej informacji, zobacz [jak: używanie kontekstu interfejsu użytkownika opartego na regułach dla rozszerzeń programu Visual Studio](../extensibility/how-to-use-rule-based-ui-context-for-visual-studio-extensions.md).  
  
## <a name="troubleshooting-vspackages"></a>Rozwiązywanie problemów z pakietami VSPackage  
 Poznaj techniki rozwiązywania problemów z usługą pakietów VSPackage, które nie ładują ani nie występują błędy: [Rozwiązywanie problemów pakietów VSPackage](../extensibility/troubleshooting-vspackages.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Pakiety VSPackage](../extensibility/internals/vspackages.md)
