---
title: Uzyskiwanie dzienników kompilacji przy użyciu programu MSBuild | Microsoft Docs
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
ms.openlocfilehash: c88288a7bed453ca14e9c14fd43706b97be04044
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64789478"
---
# <a name="obtaining-build-logs-with-msbuild"></a>Uzyskiwanie dzienników kompilacji za pomocą narzędzia MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Korzystając z przełączników w programie MSBuild, można określić, ile danych kompilacji ma być przeglądanych, oraz czy dane kompilacji mają być zapisane w jednym lub wielu plikach. Możesz również określić niestandardowy Rejestrator do zbierania danych kompilacji. Aby uzyskać informacje o przełącznikach wiersza polecenia programu MSBuild, które nie obejmują tego tematu, zobacz [informacje dotyczące wiersza polecenia](../msbuild/msbuild-command-line-reference.md).  
  
> [!NOTE]
> W przypadku kompilowania projektów przy użyciu środowiska IDE programu Visual Studio można rozwiązywać problemy z tymi kompilacjami, przeglądając dzienniki kompilacji. Aby uzyskać więcej informacji, zobacz [jak: wyświetlanie, zapisywanie i konfigurowanie plików dziennika kompilacji](../ide/how-to-view-save-and-configure-build-log-files.md).  
  
## <a name="setting-the-level-of-detail"></a>Ustawienie poziomu szczegółowości  
 Podczas kompilowania projektu przy użyciu programu MSBuild bez określania poziomu szczegółowości w dzienniku wyjściowym są wyświetlane następujące informacje:  
  
- Błędy, ostrzeżenia i komunikaty, które są klasyfikowane jako bardzo ważne.  
  
- Niektóre zdarzenia stanu.  
  
- Podsumowanie kompilacji.  
  
  Za pomocą przełącznika **/verbosity.** (**/v**) można kontrolować ilość danych wyświetlanych w dzienniku danych wyjściowych. W celu rozwiązywania problemów Użyj poziomu szczegółowości obu `detailed` ( `d` ) lub `diagnostic` ( `diag` ), który zapewnia najwięcej informacji.  
  
  Proces kompilacji może być wolniejszy, gdy ustawisz **/verbosity.** na `detailed` , a nawet wolniej po ustawieniu **/verbosity.** na `diagnostic` .  
  
```  
msbuild MyProject.proj /t:go /v:diag  
```  
  
## <a name="saving-the-build-log-to-a-file"></a>Zapisywanie dziennika kompilacji do pliku  
 Aby zapisać dane kompilacji do pliku, można użyć przełącznika **/FileLogger** (**FL**). Poniższy przykład zapisuje dane kompilacji do pliku o nazwie `msbuild.log` .  
  
```  
msbuild MyProject.proj /t:go /fileLogger  
```  
  
 W poniższym przykładzie plik dziennika ma nazwę `MyProjectOutput.log` , a poziom szczegółowości danych wyjściowych dziennika jest ustawiony na `diagnostic` . Należy określić te dwa ustawienia za pomocą przełącznika **/filelogparameters** ( `flp` ).  
  
```  
msbuild MyProject.proj /t:go /fl /flp:logfile=MyProjectOutput.log;verbosity=diagnostic  
```  
  
 Aby uzyskać więcej informacji, zobacz informacje [dotyczące wiersza polecenia](../msbuild/msbuild-command-line-reference.md).  
  
## <a name="saving-the-log-output-to-multiple-files"></a>Zapisywanie dziennika danych wyjściowych do wielu plików  
 Poniższy przykład zapisuje cały dziennik do `msbuild1.log` , tylko błędy do `JustErrors.log` i tylko ostrzeżenia do `JustWarnings.log` . W przykładzie są stosowane numery plików dla każdego z trzech plików. Numery plików są określane tuż po przełącznikach **/FL** i **/FLP** (na przykład `/fl1` i `/flp1` ).  
  
 Przełączniki **/filelogparameters** ( `flp` ) dla plików 2 i 3 określają, co należy nazwać każdy plik i co należy uwzględnić w każdym pliku. Nie określono nazwy dla pliku 1, więc `msbuild1.log` używana jest nazwa domyślna.  
  
```  
msbuild MyProject.proj /t:go /fl1 /fl2 /fl3 /flp2:logfile=JustErrors.log;errorsonly /flp3:logfile=JustWarnings.log;warningsonly  
  
```  
  
 Aby uzyskać więcej informacji, zobacz informacje [dotyczące wiersza polecenia](../msbuild/msbuild-command-line-reference.md).  
  
## <a name="using-a-custom-logger"></a>Korzystając z niestandardowego urządzenia zapisującego ciąg akcji  
 Można napisać własny rejestrator, tworząc zarządzany typ, który implementuje <xref:Microsoft.Build.Framework.ILogger> interfejs. Możesz użyć niestandardowego rejestratora, na przykład w celu wysłania błędów kompilacji w wiadomości e-mail, zarejestrowania ich w bazie danych lub zarejestrowania ich w pliku XML. Aby uzyskać więcej informacji, zobacz [rejestratory kompilacji](../msbuild/build-loggers.md).  
  
 W wierszu polecenia programu MSBuild należy określić rejestratora niestandardowego przy użyciu przełącznika **/Logger** . Można również użyć przełącznika **/noconsolelogger** , aby wyłączyć domyślny Rejestrator konsoli.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.Build.Framework.LoggerVerbosity>   
 [Rejestratory kompilacji](../msbuild/build-loggers.md)   
 [Rejestrowanie w środowisku wieloprocesorowym](../msbuild/logging-in-a-multi-processor-environment.md)   
 [Tworzenie rejestratorów przekazywania](../msbuild/creating-forwarding-loggers.md)   
 [Pojęcia dotyczące programu MSBuild](../msbuild/msbuild-concepts.md)
