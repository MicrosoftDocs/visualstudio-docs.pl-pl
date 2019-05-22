---
title: Rozszerzenia automatycznie ładowane w sposób synchroniczny
ms.date: 02/16/2019
ms.topic: conceptual
ms.assetid: 822e3cf8-f723-4ff1-8467-e0fb42358a1f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d23a19ad42f665f471274ee75f328056dd55b17d
ms.sourcegitcommit: cd21b38eefdea2cdefb53e68e7a30b868e78dd6b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2019
ms.locfileid: "66037099"
---
# <a name="synchronously-autoloaded-extensions"></a>Rozszerzenia automatycznie ładowane w sposób synchroniczny

Synchronicznie rozszerzenia załadowany automatycznie mieć negatywny wpływ na wydajność programu Visual Studio i powinny być konwertowane na zamiast tego użyj Załaduj asynchronicznego. Począwszy od programu Visual Studio 2 2019 r (wersja zapoznawcza), użytkownicy są powiadamiani, gdy rozszerzenie jest synchronicznie załadowany automatycznie. Rozszerzenie zostanie obciążenia i działają w zwykły sposób.

![Ostrzeżenie dotyczące zgodności rozszerzenia](media/extension-compatibility-warning.png)

Użytkownicy mogą:

- Kliknij pozycję **więcej** można uzyskać dostęp do tej strony informacji.

- Kliknij pozycję **zarządzanie wydajnością** otworzyć [okno dialogowe Menedżer wydajności](#performance-manager-dialog) pokazujący problemy z wydajnością za pomocą rozszerzenia i okna narzędzi.

- Kliknij pozycję **nie pokazuj ponownie tego komunikatu** aby odrzucić powiadomienie. Wybranie tej opcji uniemożliwia również wszystkich kolejnych powiadomień z synchronicznie załadowany automatycznie rozszerzeń. Użytkownicy będą w dalszym ciągu otrzymywać powiadomienia o innych funkcjach programu Visual Studio.

## <a name="performance-manager-dialog"></a>Okno dialogowe Menedżer wydajności

![okno dialogowe Menedżer wydajności](media/performance-manager.png)

Wszystkie rozszerzenia, które synchronicznie załadowane wszystkie pakiety w wszystkie sesje użytkowników są wyświetlane w **przestarzałe interfejsy API** kartę.

* Użytkownicy będą mogli kliknąć na **więcej informacji o tym problemie** zebrać więcej informacji na temat przestarzałych API.
* Użytkownicy mogą skontaktuj się z ich dostawcami rozszerzenia postęp migracji.

Twórcy rozszerzeń można znaleźć instrukcje dotyczące migracji pakietów do asynchronicznego automatyczne ładowanie na [Przeprowadź migrację do AsyncPackage](https://github.com/Microsoft/VSSDK-Extensibility-Samples/tree/master/AsyncPackageMigration).

## <a name="specify-synchronous-autoload-settings-using-group-policy"></a>Określ ustawienia Załaduj synchronicznego przy użyciu zasad grupy

Uruchamianie programu Visual Studio 2019 Update 1, domyślnie, załaduj synchroniczne bloki instalacji programu Visual Studio. Po włączeniu zasad grupy, można skonfigurować programu Visual Studio umożliwia synchroniczne automatyczne ładowanie na poszczególnych komputerach. Aby to zrobić, należy ustawić zasady opartych na rejestrze dla następującego klucza:

**HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\VisualStudio\SynchronousAutoload**

Wpis = **dozwolone**

Wartość = (DWORD)
* **0** Załaduj synchroniczne nie jest dozwolona
* **1** jest dozwolone Załaduj synchroniczne

Aby uzyskać więcej informacji na temat synchroniczne automatyczne ładowanie ustawień w Visual Studio 2019 Update 1, zobacz [synchroniczne zachowanie automatyczne ładowanie](https://aka.ms/AA52xzw) strony.
