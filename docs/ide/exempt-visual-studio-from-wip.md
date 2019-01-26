---
title: Wykluczone z Windows Information Protection
ms.date: 06/01/2018
ms.prod: visual-studio-dev15
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 65a8da50cb14850762a1bd29c8a554f9f4556ca4
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54968718"
---
# <a name="configure-visual-studio-as-a-wip-exempt-app"></a>Konfigurowanie programu Visual Studio jako aplikacja funkcji WIP wykluczone

[Windows Information Protection](/windows/security/information-protection/windows-information-protection/protect-enterprise-data-using-wip) (PWT) pomaga chronić dane organizacji przed wyciekiem do aplikacji, takich jak wiadomości e-mail, mediów społecznościowych i chmurze publicznej, będących poza kontrolą przedsiębiorstwa. Funkcja WIP ułatwia ochronę przed wyciekami danych na urządzeniach należących do przedsiębiorstwa i urządzeń osobistych bez konieczności wprowadzania zmian w środowisku lub innych aplikacji.

*Z obsługą* aplikacji funkcji WIP oczekują, aby uniemożliwić przechodząc do lokalizacji sieciowych niechronione danych przedsiębiorstwa oraz uniknąć szyfrowania danych osobowych. Program Visual Studio nie jest usprawnionych aplikacji, więc nie działa w środowiskach obsługujących funkcję WIP, o ile nie jest możliwe wykluczenie. Wykonaj kroki opisane w tym artykule, aby umożliwić programowi Visual Studio do funkcji na komputerze z włączoną funkcją WIP.

## <a name="configure-vs-as-a-wip-exempt-app"></a>Skonfiguruj program VS jako aplikacji funkcji WIP wykluczone

Można wyłączyć programu Visual Studio z ograniczenia dotyczące funkcji WIP, ale nadal zezwala na korzystanie z danych przedsiębiorstwa. Aplikacje wykluczone funkcji WIP, mogą łączyć się zasoby chmury przedsiębiorstwa przy użyciu adresu IP lub nazwa hosta. Szyfrowanie nie jest stosowana, a aplikacja może uzyskiwać dostęp do plików lokalnych.

Aby zwolnić programu Visual Studio z funkcji WIP, postępuj zgodnie z [kroki, aby zwolnić aplikację klasyczną](/windows/security/information-protection/windows-information-protection/create-wip-policy-using-intune-azure#exempt-apps-from-a-wip-policy).

## <a name="create-a-wip-exempt-applocker-policy-file"></a>Utwórz plik zasad funkcji AppLocker wykluczone funkcji WIP

Ponieważ program Visual Studio zawiera wiele plików binarnych, [Utwórz plik zasad funkcji AppLocker w funkcji WIP wykluczone](/windows/security/threat-protection/windows-defender-application-control/applocker/run-the-automatically-generate-rules-wizard). Funkcja AppLocker umożliwia automatyczne generowanie reguł dla wszystkich plików w folderze.

## <a name="add-appcompat-to-the-enterprise-cloud-resource-policy"></a>Dodaj AppCompat do zasad zasobów chmury przedsiębiorstwa

Aby określić, gdzie Visual Studio mogą uzyskać dostęp do danych przedsiębiorstwa w sieci, postępuj zgodnie z tymi [kroki, aby określić, gdzie chronionymi aplikacjami można znaleźć i wysłać danych przedsiębiorstwa](/windows/security/information-protection/windows-information-protection/create-wip-policy-using-intune-azure#choose-where-apps-can-access-enterprise-data). Aby zatrzymać Windows blokuje połączenia z chmurą zasobów za pomocą adresu IP, upewnij się, że dodawanie /\*AppCompat\*/ ciąg do ustawienia.

## <a name="see-also"></a>Zobacz także

- [Zachowanie aplikacji za pomocą funkcji WIP](/windows/security/information-protection/windows-information-protection/app-behavior-with-wip)