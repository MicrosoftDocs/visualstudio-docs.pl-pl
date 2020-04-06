---
title: Rozszerzenia automatycznie ładowane w sposób synchroniczny
ms.date: 12/11/2019
ms.topic: conceptual
ms.assetid: 822e3cf8-f723-4ff1-8467-e0fb42358a1f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ab62d235fd6ed4e47e765fc23868acd5c56efcb2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699372"
---
# <a name="synchronously-autoloaded-extensions"></a>Rozszerzenia automatycznie ładowane w sposób synchroniczny

Synchronicznie automatycznie zaakcjowane rozszerzenia mają negatywny wpływ na wydajność programu Visual Studio i powinny zostać przekonwertowane na automatyczne ładowanie asynchroniczne. Domyślnie visual studio 2019 blokuje synchronicznie automatycznie ładowane pakiety z dowolnego rozszerzenia i powiadamia użytkownika.

![ostrzeżenie o zgodności z rozszerzeniami](media/extension-compatibility-warning-16-1.png.png)

Możesz:

- Kliknij **przycisk Zezwalaj na autoload synchroniczne,** aby umożliwić rozszerzenia do automatycznego ładowania. Aby zmienić to ustawienie w opcjach programu Visual Studio, kliknij pozycję Środowisko, a następnie kliknij pozycję Rozszerzenia, a następnie zaznacz pole wyboru "Zezwalaj na synchroniczne automatyczne ładowanie rozszerzeń". 

- Kliknij **pozycję Zarządzaj wydajnością,** aby otworzyć [okno dialogowe Menedżera wydajności,](#performance-manager-dialog) w tym problemy z wydajnością z rozszerzeniami i oknami narzędzi.

- Kliknij **przycisk Nie pokazuj tego komunikatu dla bieżących rozszerzeń,** aby odrzucić powiadomienie i zapobiec przyszłym powiadomieniom z istniejących zainstalowanych rozszerzeń. Jeśli dodasz nowe rozszerzenie, które automatycznie ładuje synchronicznie, to powiadomienie zostanie wyświetlone ponownie. Będziesz nadal otrzymywać powiadomienia o innych funkcjach programu Visual Studio.

## <a name="performance-manager-dialog"></a>Okno dialogowe Menedżera wydajności

![Okno dialogowe menedżera wydajności](media/performance-manager.png)

Wszystkie rozszerzenia, które synchronicznie załadować żadnych pakietów w dowolnej sesji użytkownika są wyświetlane na karcie **Przestarzałe interfejsy API.**

* Kliknij więcej informacji na **temat tego problemu,** aby zebrać więcej informacji na temat przestarzałych interfejsów API.
* Skontaktuj się z dostawcami rozszerzeń w celu uzyskania postępu migracji.

## <a name="specify-synchronous-autoload-settings-using-group-policy"></a>Określanie ustawień automatycznego ładowania synchronicznego przy użyciu zasad grupy

Administratorzy mogą włączyć zasady grupy, aby umożliwić automatyczne ładowanie synchroniczne. Aby to zrobić, ustaw zasady oparte na rejestrze na następujący klucz:

**HKEY_LOCAL_MACHINE\SOFTWARE\Zasady\Microsoft\VisualStudio\SynchronousAutoload**

Wpis = **Dozwolone**

Wartość = (DWORD)
* **0** jest synchroniczne autoload nie jest dozwolone
* **1** jest synchroniczne automatyczne ładowanie dozwolone

## <a name="extension-authors"></a>Autorzy rozszerzeń
Autorzy rozszerzeń mogą znaleźć instrukcje dotyczące migracji pakietów do asynchronicznego automatycznego ładowania podczas [migracji do AsyncPackage](https://github.com/Microsoft/VSSDK-Extensibility-Samples/tree/master/AsyncPackageMigration).

## <a name="see-also"></a>Zobacz też
Aby uzyskać więcej informacji na temat ustawień autoładowania synchronicznego w programie Visual Studio 2019, zobacz stronę [Zachowanie autozaładania synchronicznego.](https://devblogs.microsoft.com/visualstudio/updates-to-synchronous-autoload-of-extensions-in-visual-studio-2019/)
