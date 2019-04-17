---
title: Tworzenie przekazywania rejestratorów | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, forwarding loggers
- MSBuild, logging
ms.assetid: 3aebf9c8-b62c-4cb2-b2d6-8cdfcd369a24
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ecc9bae7176c0d8c0f79452baff87a7a697db459
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/17/2019
ms.locfileid: "59648224"
---
# <a name="creating-forwarding-loggers"></a>Tworzenie przekazywania rejestratorów
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Przekazywanie rejestratorów poprawy efektywności rejestrowania, umożliwiając Ci wybrać zdarzeń, które chcesz monitorować, podczas kompilowania projektów w systemie wieloprocesorowym. Po włączeniu przekazywanie rejestratorów może uniemożliwić niepożądanych zdarzeń z przeciążenia rejestratora centralnego, spowalniając czas kompilacji i zaśmiecania dziennika.  
  
 Można utworzyć rejestratora przekazywania, można albo Implementowanie <xref:Microsoft.Build.Framework.IForwardingLogger> interfejsu, a następnie ręcznie wdrożyć jego metody lub użyj <xref:Microsoft.Build.BuildEngine.ConfigurableForwardingLogger> klasa i jej wstępnie skonfigurowanych metod. (Ten ostatni będą wystarczające dla większości aplikacji.)  
  
## <a name="register-events-and-respond-to-them"></a>Rejestrowanie zdarzeń i reagowanie na ich  
 Rejestrator przekazywania zbiera informacje o zdarzeniach kompilacji zgłoszonej przez aparat kompilacji pomocniczy, który jest proces roboczy, który jest tworzony przez proces kompilacji głównego podczas kompilacji w systemie wieloprocesorowym. Następnie rejestratora przekazywania wybiera zdarzenia do przesyłania dalej do centralnej rejestratora, zgodnie z instrukcjami, którym przyznano go.  
  
 Należy zarejestrować przekazywanie rejestratorów do obsługi zdarzeń, które chcesz monitorować. Aby rejestrować zdarzenia, należy zastąpić rejestratorów <xref:Microsoft.Build.Utilities.Logger.Initialize%2A> metody. Ta metoda obejmuje teraz opcjonalny parametr `nodecount`, które można ustawić liczby procesorów w systemie. (Domyślna wartość to 1).  
  
 Przykłady zdarzeń, które można monitorować <xref:Microsoft.Build.Framework.IEventSource.TargetStarted>, <xref:Microsoft.Build.Framework.IEventSource.ProjectStarted>, i <xref:Microsoft.Build.Framework.IEventSource.ProjectFinished>.  
  
 W środowisku wielu procesorów do odebrania poza kolejnością prawdopodobnie komunikaty o zdarzeniach. W związku z tym należy obliczyć zdarzeń za pomocą programu obsługi zdarzeń w rejestratora przekazywania i programu do określenia, które zdarzenia do przekazania do przekierowania do przekazywania danych do centralnej rejestratora. Aby to osiągnąć, można użyć <xref:Microsoft.Build.Framework.BuildEventContext> klasy, która jest dołączona do każdej wiadomości, aby ułatwić zidentyfikowanie zdarzenia, które mają być przekazywane, a następnie przekaż nazwy zdarzeń, aby <xref:Microsoft.Build.BuildEngine.ConfigurableForwardingLogger> klasy (lub podklasa go). Korzystając z tej metody, nie inne określone kodowanie jest wymagana do przesyłania dalej zdarzeń.  
  
## <a name="specify-a-forwarding-logger"></a>Określ Rejestrator przekazywania  
 Rejestrator przekazywania został wcześniej skompilowany w zestawie, musisz poinformować [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] z niego korzystać podczas kompilacji. Aby to zrobić, należy użyć `/FileLogger`, `/FileLoggerParameters`, i `/DistributedFileLogger` przełączników wraz z MSBuild.exe. `/FileLogger` MSBuild.exe informuje o przełącznikiem czy rejestrator jest bezpośrednio dołączony. `/DistributedFileLogger` Przełącznika oznacza, że istnieje plik dziennika w każdym węźle. Aby ustawić parametry rejestratora przekazywania, należy użyć `/FileLoggerParameters` przełącznika. Aby uzyskać więcej informacji na temat tych i innych przełączników MSBuild.exe, zobacz [odwołanie do wiersza polecenia](../msbuild/msbuild-command-line-reference.md).  
  
## <a name="multi-processor-aware-loggers"></a>Procesorów uwzględniających rejestratorów  
 Podczas tworzenia projektu w systemie wieloprocesorowym komunikatów kompilacji z każdego procesora nie są automatycznie przeplotu ujednoliconego sekwencji. Zamiast tego należy ustanowić komunikat grupowanie priorytet za pomocą <xref:Microsoft.Build.Framework.BuildEventContext> klasy, który jest dołączony do każdej wiadomości. Aby uzyskać więcej informacji na temat tworzenia wielu procesorów zobacz [logowanie w środowisku wielu procesorów](../msbuild/logging-in-a-multi-processor-environment.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Uzyskiwanie dzienników kompilacji](../msbuild/obtaining-build-logs-with-msbuild.md)   
 [Rejestratory kompilacji](../msbuild/build-loggers.md)   
 [Logowanie w środowisku wielu procesorów](../msbuild/logging-in-a-multi-processor-environment.md)
