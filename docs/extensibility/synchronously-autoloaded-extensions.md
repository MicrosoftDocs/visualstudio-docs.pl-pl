---
title: Rozszerzenia automatycznie ładowane w sposób synchroniczny
description: Zapoznaj się z domyślnym zachowaniem rozpoczynającym się od programu Visual Studio 2019, które blokuje synchronicznie ładowane pakiety z dowolnego rozszerzenia.
ms.custom: SEO-VS-2020
ms.date: 12/11/2019
ms.topic: conceptual
ms.assetid: 822e3cf8-f723-4ff1-8467-e0fb42358a1f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 35b63f8e84e6879d09fda4c35924b5b9d1d60ccd
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105056067"
---
# <a name="synchronously-autoloaded-extensions"></a>Rozszerzenia automatycznie ładowane w sposób synchroniczny

Synchronicznie ładowane rozszerzenia mają negatywny wpływ na wydajność programu Visual Studio i powinny być konwertowane, aby używały asynchronicznego ładowania automatyczne. Domyślnie program Visual Studio 2019 blokuje synchronicznie ładowane pakiety z dowolnego rozszerzenia i powiadamia użytkownika.

![Ostrzeżenie o zgodności rozszerzenia](media/extension-compatibility-warning-16-1.png.png)

Oto co możesz zrobić:

- Kliknij opcję **Zezwalaj na synchroniczne automatyczne ładowanie** , aby zezwalać na automatyczne ładowanie rozszerzeń. Aby zmienić to ustawienie w opcjach programu Visual Studio, kliknij pozycję środowisko, a następnie kliknij pozycję rozszerzenia, a następnie zaznacz pole wyboru "Zezwalaj na synchroniczne automatyczne ładowanie rozszerzeń". 

- Kliknij pozycję **Zarządzaj wydajnością** , aby otworzyć [okno dialogowe Menedżera wydajności](#performance-manager-dialog) , które pokazuje problemy z wydajnością za pomocą rozszerzeń i okien narzędzi.

- Kliknij pozycję **nie pokazuj tego komunikatu dla bieżących rozszerzeń** , aby odrzucić powiadomienie i uniemożliwić przyszłe powiadomienia z istniejących zainstalowanych rozszerzeń. Jeśli dodasz nowe rozszerzenie, które ładuje się synchronicznie, to powiadomienie zostanie wyświetlone ponownie. Będziesz nadal otrzymywać powiadomienia o innych funkcjach programu Visual Studio.

## <a name="performance-manager-dialog"></a>Menedżer wydajności — okno dialogowe

![Menedżer wydajności — okno dialogowe](media/performance-manager.png)

Wszystkie rozszerzenia, które synchronicznie ładowały wszystkie pakiety w dowolnych sesjach użytkownika, są wyświetlane na karcie **przestarzałe interfejsy API** .

* Kliknij **więcej informacji o tym problemie** , aby zebrać więcej informacji na temat przestarzałych interfejsów API.
* Skontaktuj się z dostawcami rozszerzeń w celu uzyskania postępu migracji.

## <a name="specify-synchronous-autoload-settings-using-group-policy"></a>Określanie ustawień synchronicznego ładowania automatyczne przy użyciu zasad grupy

Administratorzy mogą włączyć zasady grupy, aby umożliwić synchroniczne automatyczne ładowanie. W tym celu należy ustawić zasady oparte na rejestrze w następującym kluczu:

**HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\VisualStudio\SynchronousAutoload**

Wpis = **dozwolony**

Wartość = (DWORD)
* **0** to synchroniczne automatyczne ładowanie nie jest dozwolone
* **1** jest dozwolone synchroniczne automatyczne ładowanie

## <a name="extension-authors"></a>Autorzy rozszerzeń
Autorzy rozszerzeń mogą znaleźć instrukcje migrowania pakietów do asynchronicznego ładowania automatyczne podczas [migracji do AsyncPackage](https://github.com/Microsoft/VSSDK-Extensibility-Samples/tree/master/AsyncPackageMigration).

## <a name="see-also"></a>Zobacz też
Aby uzyskać więcej informacji na temat synchronicznych ustawień autoładowania w programie Visual Studio 2019, zobacz stronę [zachowanie synchronicznego ładowania automatyczne](https://devblogs.microsoft.com/visualstudio/updates-to-synchronous-autoload-of-extensions-in-visual-studio-2019/) .
