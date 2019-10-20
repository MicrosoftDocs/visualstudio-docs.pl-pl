---
title: Dane diagnostyczne i dzienniki generowane przez system
ms.date: 05/24/2018
ms.topic: conceptual
author: jillre
ms.author: michma
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9702439569fa9db1ff8687e914d5c9d20865e2b0
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652473"
---
# <a name="system-generated-logs-collected-by-visual-studio"></a>Dzienniki generowane przez system w programie Visual Studio

Program Visual Studio zbiera dzienniki generowane przez system, aby rozwiązać problemy i poprawić jakość produktu za pomocą programu [Visual Studio program poprawy jakości obsługi klienta](visual-studio-experience-improvement-program.md). Ten artykuł zawiera informacje na temat typów zbieranych danych i sposobu ich używania. Zawiera również porady dotyczące sposobu, w jaki autorzy rozszerzeń mogą uniknąć niezamierzonego ujawnienia informacji osobistych lub poufnych.

## <a name="types-of-collected-data"></a>Typy zebranych danych

Program Visual Studio zbiera dzienniki generowane przez system pod kątem awarii, zawiesza się, nie reaguje na interfejs użytkownika i duże użycie procesora CPU lub pamięci. Zbieramy również informacje o błędach napotkanych podczas instalacji lub użycia produktu. Zebrane dane różnią się w zależności od błędu i mogą obejmować ślady stosu, zrzuty pamięci i informacje o wyjątku:

- W celu zapewnienia wysokiego użycia procesora CPU i braku odpowiedzi są zbierane ślady stosu odpowiednich wątków programu Visual Studio.

- W przypadkach, gdy ślady stosu niektórych wątków nie są wystarczające, aby określić główną przyczynę problemu, na przykład awarie, zawieszenie lub wysokie użycie pamięci, zbieramy *zrzut*pamięci. Zrzut reprezentuje stan procesu, gdy wystąpił błąd.

- W przypadku nieoczekiwanych warunków błędu na przykład wyjątek podczas próby zapisu do pliku na dysku Zbieramy informacje o wyjątku. Informacje obejmują nazwę wyjątku, ślad stosu wątku, w którym wystąpił wyjątek, komunikat skojarzony z wyjątkiem i inne informacje istotne dla konkretnego wyjątku.

   Poniższy przykład zebranych danych przedstawia nazwę wyjątku, ślad stosu i komunikat o wyjątku:

   ```text
   "Reserved.DataModel.Fault.Exception.TypeString": "System.IO.IOException",
   "Reserved.DataModel.Fault.Exception.StackTrace": "System.IO.__Error.WinIOError(Int32,String)\r\n
   System.IO.FileStream.Init(String,FileMode,FileAccess,Int32,Boolean,FileShare,Int32,FileOptions,SECURITY_ATTRIBUTES,String,Boolean,Boolean,Boolean)\r\n
   System.IO.FileStream..ctor(String,FileMode,FileAccess,FileShare,Int32,FileOptions,String,Boolean,Boolean,Boolean)\r\nSystem.IO.StreamWriter.CreateFile(String,Boolean,Boolean)\r\n
   System.IO.StreamWriter..ctor(String,Boolean,Encoding,Int32,Boolean)\r\n
   System.IO.StreamWriter..ctor(String,Boolean)\r\n
   System.IO.File.CreateText(String)\r\n
   Microsoft.VisualStudio.Setup.Services.FileSystem.CreateText(String,Boolean)\r\n
   Microsoft.VisualStudio.Setup.Cache.ChannelManifestRepository.WriteChannelManifest(IChannelManifest,String,String)\r\n
   Microsoft.VisualStudio.Setup.Cache.ChannelManifestRepository.AddChannel(ChannelManifestPair,Boolean)\r\n
   Microsoft.VisualStudio.Setup.Cache.CacheManager.AddChannel(ChannelManifestPair,Boolean)\r\n
   Microsoft.VisualStudio.Setup.ChannelManager.\<UpdateAsync>d__37.MoveNext()\r\n”,
   "Reserved.DataModel.Fault.Exception.Message": " The process cannot access the file 'C:\\Users\\[UserName]\\AppData\\Local\\Microsoft\\VisualStudio\\Packages\\_Channels\\4CB340F5\\channelManifest.json' because it is being used by another process."
   ```

## <a name="how-we-use-system-generated-logs"></a>Jak korzystamy z dzienników generowanych przez system

Przepływ pracy, aby określić główną przyczynę błędu, różni się w zależności od typu błędu i jego ważności.

### <a name="error-classification"></a>Klasyfikacja błędów

Na podstawie dzienników błędy są klasyfikowane i zliczane w celu określenia priorytetów ich badania. Na przykład firma Microsoft może wykryć, że "System.IO. \__Error. WinIOError "at" System. IO. FileStream. init "wystąpiło 500 razy w wersji \<x > produktu i ma najwyższą częstotliwość występowania w tej wersji.

### <a name="work-items-for-tracking"></a>Elementy robocze do śledzenia

Elementy robocze dla pojedynczych, priorytetyzacji błędów są tworzone i przypisywane do inżynierów w celu zbadania. Te elementy robocze zwykle zawierają klasyfikację, priorytet i informacje diagnostyczne dotyczące typu błędu. Te informacje pochodzą z zebranych dzienników generowanych przez system w poszukiwaniu błędu. Na przykład element roboczy dla awarii może zawierać ślad stosu, w którym występuje awaria.

### <a name="error-investigation"></a>Badanie błędu

Inżynierowie wykorzystują informacje dostępne w elemencie roboczym, aby określić główną przyczynę błędu. W niektórych przypadkach potrzebują więcej informacji niż to, co znajduje się w elemencie roboczym, w takim przypadku odnoszą się do oryginalnego wygenerowanego przez system dziennika, który został zebrany. Na przykład inżynier może sprawdzić zrzut pamięci, aby zrozumieć awarię produktu.

## <a name="tips-for-extension-authors"></a>Porady dla autorów rozszerzeń

Autorzy rozszerzeń powinni ograniczyć narażenie na dane osobowe, nie używając osobistych lub innych poufnych informacji w nazwach modułów, typów i metod. Jeśli wystąpi awaria lub podobny warunek błędu w tym kodzie na stosie, te informacje są zbierane w ramach dzienników generowanych przez system.

## <a name="opt-out-of-data-collection"></a>Rezygnacja z zbierania danych

W oparciu o dane zbierane i ograniczenia dotyczące dostępu i przechowywania, zalecamy użycie domyślnych ustawień prywatności dla programu Visual Studio i systemu Windows. Można jednak [zrezygnować](../ide/visual-studio-experience-improvement-program.md#opt-in-or-out) z program poprawy jakości obsługi programu Visual Studio. Aby zrezygnować z wygenerowanej przez system kolekcji dzienników dla wszystkich programów, zobacz [Diagnostyka, opinie i prywatność w systemie Windows 10](https://privacy.microsoft.com/windows-10-feedback-diagnostics-and-privacy). Opcje mogą się różnić w zależności od używanej wersji systemu Windows.

## <a name="see-also"></a>Zobacz także

- [Program poprawy jakości obsługi klienta systemu Visual Studio](visual-studio-experience-improvement-program.md)
- [Diagnostyka, opinie i prywatność w systemie Windows 10](https://privacy.microsoft.com/windows-10-feedback-diagnostics-and-privacy)