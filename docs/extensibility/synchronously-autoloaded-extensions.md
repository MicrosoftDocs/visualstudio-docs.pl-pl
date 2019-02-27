---
title: Synchronicznie załadowany automatycznie rozszerzeń
ms.date: 02/16/2019
ms.topic: conceptual
ms.assetid: 822e3cf8-f723-4ff1-8467-e0fb42358a1f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 960fd54564bc25a8338461c30cd8a893e277b5a5
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2019
ms.locfileid: "56844609"
---
# <a name="synchronously-autoloaded-extensions"></a>Synchronicznie załadowany automatycznie rozszerzeń

Synchronicznie rozszerzenia załadowany automatycznie mieć negatywny wpływ na wydajność programu Visual Studio i powinny być konwertowane na zamiast tego użyj Załaduj asynchronicznego. Począwszy od programu Visual Studio 2 2019 r (wersja zapoznawcza), użytkownicy będą powiadamiani, gdy rozszerzenie jest synchronicznie załadowany automatycznie. Rozszerzenie zostanie obciążenia i działają w zwykły sposób.

![Ostrzeżenie dotyczące zgodności rozszerzenia](media/extension-compatibility-warning.png)

1. Użytkownicy będą mogli kliknąć na **więcej** można uzyskać dostęp do tej strony informacji.

3. Użytkownicy będą mogli kliknąć na **zarządzanie wydajnością** otworzyć [okno dialogowe Menedżer wydajności](#performance-manager-dialog) pokazujący problemy z wydajnością za pomocą rozszerzenia i okna narzędzi.

3. Użytkownicy będą mogli kliknąć na **nie pokazuj ponownie tego komunikatu** aby odrzucić powiadomienie. Wybranie tej opcji spowoduje również wszystkich kolejnych powiadomień z synchronicznie załadowany automatycznie rozszerzeń. Użytkownicy będą w dalszym ciągu otrzymywać powiadomienia na inne funkcje programu Visual Studio.

### <a name="performance-manager-dialog"></a>Okno dialogowe Menedżer wydajności

  ![okno dialogowe Menedżer wydajności](media/performance-manager.png)

Wszystkie rozszerzenia, które synchronicznie załadowane wszystkie pakiety w innych sesji użytkownika będzie wyświetlana w **przestarzałe interfejsy API** kartę.

* Użytkownicy będą mogli kliknąć na **więcej informacji o tym problemie** zebrać więcej informacji na temat przestarzałych API.
* Użytkownicy mogą skontaktuj się z ich dostawcami rozszerzenia postęp migracji.

Twórcy rozszerzeń można znaleźć instrukcje dotyczące migracji pakietów do asynchronicznego automatyczne ładowanie na [Przeprowadź migrację do AsyncPackage](https://github.com/Microsoft/VSSDK-Extensibility-Samples/tree/master/AsyncPackageMigration).
