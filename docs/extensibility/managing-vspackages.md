---
title: Zarządzanie pakietami VSPackage | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, autoloading
- VSPackages, delayed loading
- delay loading
- VSPackages, loading
ms.assetid: 386e0ce5-4107-4164-b0cd-1cf43eb5e7cf
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c07e3924db75f870910e22aee8c913f5a26a7411
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53822294"
---
# <a name="manage-vspackages"></a>Zarządzanie pakietami VSPackage
W większości przypadków nie trzeba martwić się o zarządzaniu pakietami VSPackage, ponieważ szablony projektów i elementów Zarejestruj i automatycznie załadować pakietu. Jednak w niektórych sytuacjach konieczne może się nieco więcej, aby można było zarządzać pakietu.  
  
## <a name="use-the-experimental-instance"></a>Użyj wystąpienie eksperymentalne  
 Aby dowiedzieć się więcej na temat wystąpienia eksperymentalnego, zobacz [wystąpienie doświadczalne](../extensibility/the-experimental-instance.md).  
  
## <a name="register-and-unregister-vspackages"></a>Rejestrowanie i wyrejestrowywanie pakietów VSPackage  
 Aby dowiedzieć się, jak rejestrowanie i wyrejestrowywanie pakietów VSPackage i innych rodzajów rozszerzenia, zobacz [rejestrowanie i wyrejestrowywanie pakietów VSPackage](../extensibility/registering-and-unregistering-vspackages.md).  
  
## <a name="load-a-vspackage"></a>Ładowanie pakietu VSPackage  
 Pakietów VSPackage, który można ustawić automatyczne ładowanie podczas określonego identyfikatora GUID CMDUICONTEXT jest włączone. Aby uzyskać więcej informacji, zobacz [ładowanie pakietów VSPackage](../extensibility/loading-vspackages.md).  
  
## <a name="use-asyncpackage-to-load-vspackages-in-the-background"></a>Używanie klasy AsyncPackage do ładowania pakietów VSPackages w tle  
 `AsyncPackage` Klasa umożliwia ładowanie pakiet w wątku w tle dla szybsza reakcja interfejsu użytkownika w programie Visual Studio. Aby uzyskać więcej informacji, zobacz [jak: Używanie klasy AsyncPackage do ładowania pakietów VSPackages w tle](../extensibility/how-to-use-asyncpackage-to-load-vspackages-in-the-background.md).  
  
## <a name="rule-based-ui-context-for-extensions"></a>Oparty na regułach kontekstu interfejsu użytkownika dla rozszerzenia  
 Konteksty interfejsu użytkownika opartego na regułach umożliwia autorom rozszerzenia do definiowania dokładne warunki, na jakich kontekstu interfejsu użytkownika jest aktywowany, a następnie załadować skojarzonych pakietów VSPackage. Aby uzyskać więcej informacji, zobacz [jak: Użyj kontekstu interfejsu użytkownika opartego na regułach dla rozszerzeń programu Visual Studio](../extensibility/how-to-use-rule-based-ui-context-for-visual-studio-extensions.md).  
  
## <a name="diagnose-extension-performance"></a>Diagnozowanie wydajności rozszerzenia  
Rozszerzenia może wpłynąć na wydajność obciążenia uruchamiania i rozwiązania. Dowiedz się, jak jest obliczana wpływ rozszerzenia programu Visual Studio i jak można je analizować lokalnie, aby sprawdzić, czy rozszerzenia mogą być wyświetlane jako wydajności, wpływ na rozszerzenia. Aby uzyskać więcej informacji, zobacz [jak: Diagnozowanie wydajności rozszerzenia](how-to-diagnose-extension-performance.md). 
  
## <a name="troubleshoot-vspackages"></a>Rozwiązywanie problemów z pakietami VSPackage  
 Dowiedz się techniki rozwiązywania problemów z pakietami VSPackage, które nie są ładowane lub występują błędy: [Rozwiązywanie problemów z pakietami VSPackage](../extensibility/troubleshooting-vspackages.md)  
  
## <a name="see-also"></a>Zobacz także  
 [Pakiety VSPackage](../extensibility/internals/vspackages.md)