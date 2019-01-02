---
title: Tworzenie przekazywania rejestratorów | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, forwarding loggers
- MSBuild, logging
ms.assetid: 3aebf9c8-b62c-4cb2-b2d6-8cdfcd369a24
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f7bb2519389503be10bbab57a3ea97fb3b0609d4
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53936558"
---
# <a name="create-forwarding-loggers"></a>Tworzenie przekazywania rejestratorów
Przekazywanie rejestratorów poprawy efektywności rejestrowania, umożliwiając Ci wybrać zdarzeń, które chcesz monitorować, podczas kompilowania projektów w systemie wieloprocesorowym. Po włączeniu przekazywanie rejestratorów może uniemożliwić niepożądanych zdarzeń z przeciążenia rejestratora centralnego, spowalniając czas kompilacji i zaśmiecania dziennika.  
  
 Można utworzyć rejestratora przekazywania, można albo Implementowanie <xref:Microsoft.Build.Framework.IForwardingLogger> interfejsu, a następnie ręcznie wdrożyć jego metody lub użyj <xref:Microsoft.Build.BuildEngine.ConfigurableForwardingLogger> klasa i jej wstępnie skonfigurowanych metod. (Ten ostatni będą wystarczające dla większości aplikacji.)  
  
## <a name="register-events-and-respond-to-them"></a>Rejestrowanie zdarzeń i Reaguj na nie  
 Rejestrator przekazywania zbiera informacje o zdarzeniach kompilacji zgłoszonej przez aparat kompilacji pomocniczy, który jest proces roboczy, który jest tworzony przez proces kompilacji głównego podczas kompilacji w systemie wieloprocesorowym. Następnie rejestratora przekazywania wybiera zdarzenia do przesyłania dalej do centralnej rejestratora, zgodnie z instrukcjami, którym przyznano go.  
  
 Należy zarejestrować przekazywanie rejestratorów do obsługi zdarzeń, które chcesz monitorować. Aby rejestrować zdarzenia, należy zastąpić rejestratorów <xref:Microsoft.Build.Utilities.Logger.Initialize%2A> metody. Ta metoda obejmuje teraz opcjonalny parametr `nodecount`, które można ustawić liczby procesorów w systemie. (Domyślna wartość to 1).  
  
 Przykłady zdarzeń, które można monitorować <xref:Microsoft.Build.Framework.IEventSource.TargetStarted>, <xref:Microsoft.Build.Framework.IEventSource.ProjectStarted>, i <xref:Microsoft.Build.Framework.IEventSource.ProjectFinished>.  
  
 W środowisku wielu procesorów do odebrania poza kolejnością prawdopodobnie komunikaty o zdarzeniach. W związku z tym należy obliczyć zdarzeń za pomocą programu obsługi zdarzeń w rejestratora przekazywania i programu do określenia, które zdarzenia do przekazania do przekierowania do przekazywania danych do centralnej rejestratora. Aby to osiągnąć, można użyć <xref:Microsoft.Build.Framework.BuildEventContext> klasy, która jest dołączona do każdej wiadomości, aby ułatwić zidentyfikowanie zdarzenia, które mają być przekazywane, a następnie przekaż nazwy zdarzeń, aby <xref:Microsoft.Build.BuildEngine.ConfigurableForwardingLogger> klasy (lub podklasa go). Korzystając z tej metody, nie inne określone kodowanie jest wymagana do przesyłania dalej zdarzeń.  
  
## <a name="specify-a-forwarding-logger"></a>Określ Rejestrator przekazywania  
 Rejestrator przekazywania został wcześniej skompilowany w zestawie, musisz poinformować [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] z niego korzystać podczas kompilacji. Aby to zrobić, należy użyć `-FileLogger`, `-FileLoggerParameters`, i `-DistributedFileLogger` zmienia się wraz z *MSBuild.exe*. `-FileLogger` Informuje o przełącznikiem *MSBuild.exe* bezpośrednio dołączonego rejestratora. `-DistributedFileLogger` Przełącznika oznacza, że istnieje plik dziennika w każdym węźle. Aby ustawić parametry rejestratora przekazywania, należy użyć `-FileLoggerParameters` przełącznika. Aby uzyskać więcej informacji na temat tych i innych *MSBuild.exe* przełączników, zobacz [wiersza polecenia](../msbuild/msbuild-command-line-reference.md).  
  
## <a name="multi-processor-aware-loggers"></a>Procesorów uwzględniających rejestratorów  
 Podczas tworzenia projektu w systemie wieloprocesorowym komunikatów kompilacji z każdego procesora nie są automatycznie przeplotu ujednoliconego sekwencji. Zamiast tego należy ustanowić komunikat grupowanie priorytet za pomocą <xref:Microsoft.Build.Framework.BuildEventContext> klasy, który jest dołączony do każdej wiadomości. Aby uzyskać więcej informacji na temat tworzenia wielu procesorów zobacz [logowanie w środowisku wielu procesorów](../msbuild/logging-in-a-multi-processor-environment.md).  
  
## <a name="see-also"></a>Zobacz także  
 [Uzyskiwanie dzienników kompilacji](../msbuild/obtaining-build-logs-with-msbuild.md)   
 [Rejestratory kompilacji](../msbuild/build-loggers.md)   
 [Logowanie w środowisku wielu procesorów](../msbuild/logging-in-a-multi-processor-environment.md)