---
title: Dane diagnostyczne i dzienniki generowane przez system
ms.date: 05/24/2018
ms.topic: conceptual
author: gewarren
ms.author: michma
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0f92e899ff8e56c68fcf1a4ab639d027c139afcf
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62557401"
---
# <a name="system-generated-logs-collected-by-visual-studio"></a>Dzienniki generowane przez system, zebrane przez program Visual Studio

Program Visual Studio zbiera dzienniki generowane przez system do rozwiązywania problemów i poprawić jakość produktu za pośrednictwem [programu poprawy jakości obsługi klienta programu Visual Studio](visual-studio-experience-improvement-program.md). W tym artykule udostępniono pewne informacje o typach danych, które zbieramy, i jak firma Microsoft używa. Zawiera także wskazówki dotyczące sposobu twórcy rozszerzeń można uniknąć przypadkowego ujawnienia informacji osobistych lub poufnych.

## <a name="types-of-collected-data"></a>Typy zebranych danych

Program Visual Studio zbiera dzienniki generowane przez system dla awarii, zawieszenia, brak reakcji interfejsu użytkownika i wysokie użycie procesora CPU lub pamięci. Zbierane są również informacje na temat błędów napotkanych podczas instalacji produktu lub użycia. Zebrane dane w zależności od błędu i mogą obejmować następujące ślady stosu, zrzuty pamięci i informacje o wyjątku:

- Wysokie użycie procesora CPU i sek ślady stosu, odpowiednie wątków programu Visual Studio są zbierane.

- Przypadki, w którym ślady stosu wątków nie są wystarczająco dużo, aby określić katalog główny przyczyną problemu, na przykład awarii zawiesza się lub wysokie użycie pamięci, Trwa zbieranie pamięci *zrzutu*. Zrzutu reprezentuje stan procesu w momencie wystąpienia błędu.

- Nieoczekiwany błąd warunki, na przykład wyjątek podczas próby zapisania pliku na dysku, zbierane są informacje o wyjątku. Informacje obejmują nazwę wyjątku, ślad stosu wątku, w którym wystąpił wyjątek, komunikat skojarzony z wyjątku i inne informacje, które są istotne dla określonego wyjątku.

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

## <a name="how-we-use-system-generated-logs"></a>Jak firma Microsoft używa dzienników generowanych przez system

Przepływ pracy, aby ustalić przyczynę błędu różni się w zależności od rodzaju błąd i jego ważności.

### <a name="error-classification"></a>Błąd klasyfikacji

Oparte na dziennikach, błędy są klasyfikowane i zliczane, do badania ich priorytety. Na przykład firma Microsoft może stwierdzić, że "System.IO. \__Error.WinIOError "na"System.IO.FileStream.Init"Wystąpił 500 razy w wersji \<x > produktu, i ma najwyższy stopień wystąpienie w tej wersji.

### <a name="work-items-for-tracking"></a>Elementy robocze do śledzenia

Elementy robocze dla indywidualnych, priorytetyzacji błędy zostały utworzone i przypisane do inżynierów w celu zbadania problemu. Te elementy robocze, zwykle zawierają klasyfikacji, priorytetu i informacje diagnostyczne, które są istotne dla typu błędu. Informacja ta jest tworzony na podstawie zebranych dzienników generowanych przez system dla błędu. Na przykład element roboczy dla awarii może zawierać ślad stosu, gdzie występuje awaria.

### <a name="error-investigation"></a>Błąd podczas badania

Inżynierowie skorzystaj z informacji, które są dostępne w elemencie roboczym ustalania głównej przyczyny błędu. W niektórych przypadkach potrzebują więcej informacji, niż co to jest obecny w elemencie roboczym, w którym to przypadku odnoszą się do oryginalnego dziennika generowanych przez system, które zostały zebrane. Na przykład inżynier może sprawdzić zrzut pamięci, aby zrozumieć awarię produktu.

## <a name="tips-for-extension-authors"></a>Porady dotyczące twórcy rozszerzeń

Twórcy rozszerzeń należy ograniczyć narażenie informacje osobiste, nie korzystając osobistych lub inne poufne informacje w nazwach swoich modułów, typów i metod. Sytuacji awarię lub podobne warunku błędu z tym kodem na stosie, te informacje pobiera zbierane w ramach dzienników generowanych przez system.

## <a name="opt-out-of-data-collection"></a>Zrezygnować ze zbierania danych

Biorąc pod uwagę cel zbieranych danych oraz ograniczenia dotyczące jego dostępu i przechowywania, zalecane jest użycie domyślnych ustawień prywatności dla programu Visual Studio i Windows. Można jednak [zrezygnować](../ide/visual-studio-experience-improvement-program.md#opt-in-or-out) z programu poprawy jakości obsługi programu Visual Studio. Aby zrezygnować z zbieranie dzienników generowanych przez system dla wszystkich programów, zobacz [diagnostyki, opinie i ochrony prywatności w systemie Windows 10](https://privacy.microsoft.com/windows-10-feedback-diagnostics-and-privacy). Opcje mogą się różnić w zależności od wersji Windows używasz.

## <a name="see-also"></a>Zobacz także

- [Program poprawy jakości obsługi klienta systemu Visual Studio](visual-studio-experience-improvement-program.md)
- [Diagnostyka, opinie i ochrony prywatności w systemie Windows 10](https://privacy.microsoft.com/windows-10-feedback-diagnostics-and-privacy)