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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "72652473"
---
# <a name="system-generated-logs-collected-by-visual-studio"></a>Dzienniki generowane przez system zebrane przez program Visual Studio

Program Visual Studio zbiera dzienniki generowane przez system, aby rozwiązać problemy i poprawić jakość produktu za pośrednictwem [programu poprawy jakości obsługi klienta programu Visual Studio.](visual-studio-experience-improvement-program.md) Ten artykuł zawiera informacje na temat rodzajów gromadzonych przez nas danych i sposobu ich wykorzystywania. Zawiera również wskazówki, w jaki sposób autorzy rozszerzenia mogą uniknąć nieumyślnego ujawnienia informacji osobistych lub poufnych.

## <a name="types-of-collected-data"></a>Rodzaje gromadzonych danych

Visual Studio zbiera dzienniki generowane przez system dla awarii, zawiesza się, nie odpowiada na interfejs użytkownika i wysokie użycie procesora CPU lub pamięci. Gromadzimy również informacje o błędach napotkanych podczas instalacji lub użytkowania produktu. Zebrane dane różnią się w zależności od błędu i mogą obejmować ślady stosu, zrzuty pamięci i informacje o wyjątkach:

- Dla wysokiego użycia procesora CPU i braku odpowiedzi śledzenia stosu odpowiednich wątków programu Visual Studio są zbierane.

- W przypadkach, gdy ślady stosu niektórych wątków nie są wystarczające do określenia głównej przyczyny problemu, na przykład awarii, zawiesza się lub wysokiego użycia pamięci, zbieramy *zrzut*pamięci. Zrzut reprezentuje stan procesu, gdy wystąpił błąd.

- W przypadku nieoczekiwanych warunków błędu, na przykład wyjątek podczas próby zapisu do pliku na dysku, zbieramy informacje o wyjątku. Informacje obejmują nazwę wyjątku, ślad stosu wątku, w którym wystąpił wyjątek, komunikat skojarzony z wyjątkiem i inne informacje istotne dla określonego wyjątku.

   Poniższy przykład zebranych danych przedstawia nazwę wyjątku, śledzenie stosu i komunikat o wyjątku:

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

## <a name="how-we-use-system-generated-logs"></a>Jak wykorzystujemy dzienniki generowane przez system

Przepływ pracy w celu określenia głównej przyczyny błędu różni się w zależności od typu błędu i jego ważności.

### <a name="error-classification"></a>Klasyfikacja błędów

Na podstawie dzienników błędy są klasyfikowane i liczone do priorytetowego określania priorytetów ich dochodzenia. Na przykład możemy odkryć, że "System.IO. \__Error.WinIOError" w "System.IO.FileStream.Init" wystąpił 500 razy \<w wersji x> produktu i ma najwyższy wskaźnik występowania w tej wersji.

### <a name="work-items-for-tracking"></a>Elementy robocze do śledzenia

Elementy pracy dla poszczególnych, priorytetowe błędy są tworzone i przypisywane do inżynierów do badania. Te elementy robocze zazwyczaj zawierają klasyfikację, priorytet i informacje diagnostyczne istotne dla typu błędu. Te informacje pochodzą z zebranych dzienników generowanych przez system dla błędu. Na przykład element pracy dla awarii może zawierać śledzenia stosu, gdzie występuje awaria.

### <a name="error-investigation"></a>Badanie błędów

Inżynierowie używają informacji dostępnych w elemencie roboczym, aby określić główną przyczynę błędu. W niektórych przypadkach potrzebują więcej informacji niż to, co jest obecne w elemencie pracy, w którym to przypadku odnoszą się do oryginalnego dziennika wygenerowanego przez system, który został zebrany. Na przykład inżynier może sprawdzić zrzut pamięci, aby zrozumieć awarię produktu.

## <a name="tips-for-extension-authors"></a>Wskazówki dla autorów rozszerzeń

Autorzy rozszerzeń powinni ograniczyć narażenie na dane osobowe, nie używając danych osobowych lub innych poufnych informacji w nazwach swoich modułów, typów i metod. Jeśli wystąpi awaria lub podobny warunek błędu z tym kodem na stosie, informacje te są zbierane jako część dzienników generowanych przez system.

## <a name="opt-out-of-data-collection"></a>Rezygnacja z gromadzenia danych

Biorąc pod uwagę cel gromadzonych danych oraz ograniczenia dotyczące ich dostępu i przechowywania, zaleca się użycie domyślnych ustawień prywatności dla programów Visual Studio i Windows. Można jednak [zrezygnować z](../ide/visual-studio-experience-improvement-program.md#opt-in-or-out) programu poprawy środowiska programu Visual Studio. Aby zrezygnować z generowania dzienników generowanych przez system dla wszystkich programów, zobacz [Diagnostyka, opinie i prywatność w systemie Windows 10](https://privacy.microsoft.com/windows-10-feedback-diagnostics-and-privacy). Opcje mogą się różnić w zależności od używanej wersji systemu Windows.

## <a name="see-also"></a>Zobacz też

- [Program poprawy jakości obsługi klienta systemu Visual Studio](visual-studio-experience-improvement-program.md)
- [Diagnostyka, opinie i prywatność w systemie Windows 10](https://privacy.microsoft.com/windows-10-feedback-diagnostics-and-privacy)