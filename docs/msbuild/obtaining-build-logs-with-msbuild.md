---
title: Uzyskiwanie dzienników kompilacji przy użyciu programu MSBuild | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, logging
- logging [MSBuild]
ms.assetid: 6ba9a754-9cc0-4fed-9fc8-4dcd3926a031
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e3dad3a9b157989ecf993cf951f91fc6296ecdf7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "88238611"
---
# <a name="obtain-build-logs-with-msbuild"></a>Uzyskiwanie dzienników kompilacji przy użyciu programu MSBuild

Korzystając z przełączników w programie MSBuild, można określić, ile danych kompilacji ma być przeglądanych, oraz czy dane kompilacji mają być zapisane w jednym lub wielu plikach. Możesz również określić niestandardowy Rejestrator do zbierania danych kompilacji. Aby uzyskać informacje o przełącznikach wiersza polecenia programu MSBuild, które nie obejmują tego tematu, zobacz [informacje dotyczące wiersza polecenia](../msbuild/msbuild-command-line-reference.md).

> [!NOTE]
> W przypadku kompilowania projektów przy użyciu środowiska IDE programu Visual Studio można rozwiązywać problemy z tymi kompilacjami, przeglądając dzienniki kompilacji. Aby uzyskać więcej informacji, zobacz [jak: wyświetlanie, zapisywanie i konfigurowanie plików dziennika kompilacji](../ide/how-to-view-save-and-configure-build-log-files.md).

## <a name="set-the-level-of-detail"></a>Ustawianie poziomu szczegółowości

 Podczas kompilowania projektu przy użyciu programu MSBuild bez określania poziomu szczegółowości w dzienniku wyjściowym są wyświetlane następujące informacje:

- Błędy, ostrzeżenia i komunikaty, które są klasyfikowane jako bardzo ważne.

- Niektóre zdarzenia stanu.

- Podsumowanie kompilacji.

Za pomocą przełącznika **-verbose** (**-v**) można kontrolować ilość danych wyświetlanych w dzienniku danych wyjściowych. W celu rozwiązywania problemów Użyj poziomu szczegółowości obu `detailed` ( `d` ) lub `diagnostic` ( `diag` ), który zapewnia najwięcej informacji.

Proces kompilacji może być wolniejszy, gdy ustawisz poziom **szczegółowości** na `detailed` , a nawet wolniej, gdy ustawisz poziom **szczegółowości** na `diagnostic` .

```cmd
msbuild MyProject.proj -t:go -v:diag
```

### <a name="verbosity-settings"></a>Ustawienia szczegółowości

W poniższej tabeli przedstawiono, w jaki sposób poziom szczegółowości dziennika (wartości kolumn) ma wpływ na to, które typy komunikatów (wartości wierszy) są rejestrowane.

| Typ komunikatu/poziom szczegółowości              | Quiet | Minimalny | Normalne | szczegółowo | Diagnostyka |
|---------------------------------------|:-----:|:-------:|:------:|:--------:|:----------:|
| błędy                                |   ✅   |    ✅    |    ✅   |     ✅    |      ✅     |
| Ostrzeżenia                              |   ✅   |    ✅    |    ✅   |     ✅    |      ✅     |
| Komunikaty o wysokiej ważności              |       |    ✅    |    ✅   |     ✅    |      ✅     |
| Komunikaty o normalnej ważności           |       |         |    ✅   |     ✅    |      ✅     |
| Komunikaty o niskiej ważności              |       |         |        |     ✅    |      ✅     |
| Dodatkowe informacje o aparacie MSBuild |       |         |        |          |      ✅     |

## <a name="save-the-build-log-to-a-file"></a>Zapisz dziennik kompilacji w pliku

Aby zapisać dane kompilacji do pliku, można użyć przełącznika **-FileLogger** (**FL**). Poniższy przykład zapisuje dane kompilacji do pliku o nazwie *MSBuild. log*.

```cmd
msbuild MyProject.proj -t:go -fileLogger
```

 W poniższym przykładzie plik dziennika ma nazwę *MyProjectOutput. log*, a poziom szczegółowości danych wyjściowych dziennika jest ustawiony na `diagnostic` . Należy określić te dwa ustawienia za pomocą przełącznika **-fileLoggerParameters** ( `flp` ).

```cmd
msbuild MyProject.proj -t:go -fl -flp:logfile=MyProjectOutput.log;verbosity=diagnostic
```

 Aby uzyskać więcej informacji, zobacz informacje [dotyczące wiersza polecenia](../msbuild/msbuild-command-line-reference.md).

## <a name="save-the-log-output-to-multiple-files"></a>Zapisz dane wyjściowe dziennika w wielu plikach

 Poniższy przykład zapisuje cały dziennik do *msbuild1. log*, tylko błędy do *JustErrors. log*i tylko ostrzeżenia do *JustWarnings. log*. W przykładzie są stosowane numery plików dla każdego z trzech plików. Numery plików są określane bezpośrednio po przełącznikach **-FL** i **-FLP** (na przykład `-fl1` i `-flp1` ).

 Przełączniki **-fileLoggerParameters** ( `flp` ) dla plików 2 i 3 określają, co należy nazwać każdy plik i co należy uwzględnić w każdym pliku. Nie określono nazwy dla pliku 1, więc jest używana domyślna nazwa *msbuild1. log* .

```cmd
msbuild MyProject.proj -t:go -fl1 -fl2 -fl3 -flp2:logfile=JustErrors.log;errorsonly -flp3:logfile=JustWarnings.log;warningsonly
```

 Aby uzyskać więcej informacji, zobacz informacje [dotyczące wiersza polecenia](../msbuild/msbuild-command-line-reference.md).

## <a name="save-a-binary-log"></a>Zapisz dziennik binarny

Dziennik można zapisać w skompresowanym formacie binarnym przy użyciu przełącznika **-binaryLogger** (**BL**). Ten dziennik zawiera szczegółowy opis procesu kompilacji i może zostać odczytany przez niektóre narzędzia do analizy dzienników.

W poniższym przykładzie jest tworzony binarny plik dziennika o nazwie *binarylogfilename*.

```cmd
-bl:binarylogfilename.binlog
```

Aby uzyskać więcej informacji, zobacz informacje [dotyczące wiersza polecenia](../msbuild/msbuild-command-line-reference.md).

## <a name="use-a-custom-logger"></a>Korzystanie z rejestratora niestandardowego

 Można napisać własny rejestrator, tworząc zarządzany typ, który implementuje <xref:Microsoft.Build.Framework.ILogger> interfejs. Możesz użyć niestandardowego rejestratora, na przykład w celu wysłania błędów kompilacji w wiadomości e-mail, zarejestrowania ich w bazie danych lub zarejestrowania ich w pliku XML. Aby uzyskać więcej informacji, zobacz [rejestratory kompilacji](../msbuild/build-loggers.md).

 W wierszu polecenia programu MSBuild należy określić rejestratora niestandardowego przy użyciu przełącznika **-rejestratora** . Aby wyłączyć domyślny rejestratora konsoli, można również użyć przełącznika **-noconsolelogger** .

## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.Build.Framework.LoggerVerbosity>
- [Rejestratory kompilacji](../msbuild/build-loggers.md)
- [Rejestrowanie w środowisku wieloprocesorowym](../msbuild/logging-in-a-multi-processor-environment.md)
- [Tworzenie rejestratorów przekazujących](../msbuild/creating-forwarding-loggers.md)
- [Pojęcia dotyczące programu MSBuild](../msbuild/msbuild-concepts.md)
