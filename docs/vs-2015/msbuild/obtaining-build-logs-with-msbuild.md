---
title: Uzyskiwanie kompilacja dzienników za pomocą narzędzia MSBuild | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, logging
- logging [MSBuild]
ms.assetid: 6ba9a754-9cc0-4fed-9fc8-4dcd3926a031
caps.latest.revision: 30
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5ee565786f4a1f7c1127217eeb551352ae02b72f
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/17/2019
ms.locfileid: "59663417"
---
# <a name="obtaining-build-logs-with-msbuild"></a>Uzyskiwanie dzienników kompilacji za pomocą narzędzia MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Za pomocą przełączników za pomocą narzędzia MSBuild, można określić ilość danych kompilacji, aby Przegląd i czy chcesz zapisać dane kompilacji do jednego lub więcej plików. Można również określić niestandardowe rejestratora zbierania danych o kompilacji. Aby uzyskać informacje dotyczące przełączników wiersza polecenia programu MSBuild, które ten temat nie obejmuje, zobacz [odwołanie do wiersza polecenia](../msbuild/msbuild-command-line-reference.md).  
  
> [!NOTE]
>  Jeśli tworzysz projektów za pomocą programu Visual Studio IDE tych kompilacji można rozwiązać, przeglądając dzienniki kompilacji. Aby uzyskać więcej informacji, zobacz [jak: Wyświetlanie, zapisywanie i konfigurowanie plików dziennika kompilacji](../ide/how-to-view-save-and-configure-build-log-files.md).  
  
## <a name="setting-the-level-of-detail"></a>Ustawienie poziomu szczegółowości  
 Gdy tworzysz projekt za pomocą programu MSBuild bez określania poziomu szczegółowości zostaną wyświetlone następujące informacje w dzienniku danych wyjściowych:  
  
- Błędy, ostrzeżenia i komunikaty, które są klasyfikowane jako bardzo ważne.  
  
- Niektóre zdarzenia stanu.  
  
- Podsumowanie kompilacji.  
  
  Za pomocą **/verbosity** (**/v**) przełączyć, można kontrolować, jak dużo danych pojawia się w dzienniku danych wyjściowych. Do rozwiązywania problemów, należy użyć poziom szczegółowości, albo `detailed` (`d`) lub `diagnostic` (`diag`), zapewniającą najwięcej informacji.  
  
  Proces kompilacji może być niższa, po ustawieniu **/verbosity** do `detailed` i nawet wolniej, po ustawieniu **/verbosity** do `diagnostic`.  
  
```  
msbuild MyProject.proj /t:go /v:diag  
```  
  
## <a name="saving-the-build-log-to-a-file"></a>Zapisywanie dziennika kompilacji do pliku  
 Możesz użyć **/fileLogger** (**fl**) przełącznik, aby zapisać dane kompilacji do pliku. Poniższy przykład zapisuje dane kompilacji do pliku, który nosi nazwę `msbuild.log`.  
  
```  
msbuild MyProject.proj /t:go /fileLogger  
```  
  
 W poniższym przykładzie plik dziennika o nazwie `MyProjectOutput.log`, a poziom szczegółowości danych wyjściowych dziennika jest ustawione na `diagnostic`. Należy określić te dwa ustawienia za pomocą **/filelogparameters** (`flp`) przełącznika.  
  
```  
msbuild MyProject.proj /t:go /fl /flp:logfile=MyProjectOutput.log;verbosity=diagnostic  
```  
  
 Aby uzyskać więcej informacji, zobacz [odwołanie do wiersza polecenia](../msbuild/msbuild-command-line-reference.md).  
  
## <a name="saving-the-log-output-to-multiple-files"></a>Zapisywanie dziennika danych wyjściowych do wielu plików  
 Poniższy przykład zapisuje cały dziennik, aby `msbuild1.log`, po prostu błędy do `JustErrors.log`i po prostu ostrzeżeń do `JustWarnings.log`. W przykładzie użyto liczby plików dla każdego z trzech plików. Liczby plików są określane tylko po **/fl** i **/flp** przełączników (na przykład `/fl1` i `/flp1`).  
  
 **/Filelogparameters** (`flp`) przełącza dla plików, 2 i 3, określ, jakie nazwę każdego pliku i co należy uwzględnić w każdym pliku. Nie określono nazwy dla pliku 1, więc domyślną nazwę `msbuild1.log` jest używany.  
  
```  
msbuild MyProject.proj /t:go /fl1 /fl2 /fl3 /flp2:logfile=JustErrors.log;errorsonly /flp3:logfile=JustWarnings.log;warningsonly  
  
```  
  
 Aby uzyskać więcej informacji, zobacz [odwołanie do wiersza polecenia](../msbuild/msbuild-command-line-reference.md).  
  
## <a name="using-a-custom-logger"></a>Korzystając z niestandardowego urządzenia zapisującego ciąg akcji  
 Można napisać własne rejestratora, tworząc typ zarządzany, który implementuje <xref:Microsoft.Build.Framework.ILogger> interfejsu. Można na przykład użyć Rejestrator niestandardowych, wysłać błędy kompilacji w wiadomości e-mail, rejestrować je do bazy danych lub dziennika je do pliku XML. Aby uzyskać więcej informacji, zobacz [rejestratory kompilacji](../msbuild/build-loggers.md).  
  
 W wierszu polecenia programu MSBuild, należy określić Rejestrator niestandardowych za pomocą **/logger** przełącznika. Można również użyć **/noconsolelogger** przełącznik wyłączający rejestratora konsoli do domyślnego.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.Build.Framework.LoggerVerbosity>   
 [Rejestratory kompilacji](../msbuild/build-loggers.md)   
 [Logowanie w środowisku wielu procesorów](../msbuild/logging-in-a-multi-processor-environment.md)   
 [Tworzenie przekazywania rejestratorów](../msbuild/creating-forwarding-loggers.md)   
 [Pojęcia dotyczące programu MSBuild](../msbuild/msbuild-concepts.md)
