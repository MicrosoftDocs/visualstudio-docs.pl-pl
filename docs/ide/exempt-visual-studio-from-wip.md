---
title: Wykluczony z Information Protection systemu Windows
description: Dowiedz się więcej na temat wykluczania programu Visual Studio z systemu Windows Information Protection i nadal zezwala na korzystanie z danych przedsiębiorstwa.
ms.custom: SEO-VS-2020
ms.date: 06/01/2018
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 34765cc7ac303bd44c3c4ccca87ea7c00a36ccda
ms.sourcegitcommit: d6207a3a590c9ea84e3b25981d39933ad5f19ea3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/24/2020
ms.locfileid: "95598396"
---
# <a name="configure-visual-studio-as-a-wip-exempt-app"></a>Konfigurowanie programu Visual Studio jako aplikacji z wykluczeniem PWT

[System Windows Information Protection](/windows/security/information-protection/windows-information-protection/protect-enterprise-data-using-wip) (PWT) pomaga chronić dane przedsiębiorstwa przed wyciekiem przez aplikacje takie jak poczta e-mail, Media społecznościowe i chmura publiczna, które są poza kontrolą przedsiębiorstwa. PWT pomaga chronić przed przypadkowym wyciekem danych na urządzeniach należących do przedsiębiorstwa i urządzeniach osobistych, bez konieczności wprowadzania zmian w środowisku lub innych aplikacjach.

Oczekuje się, że aplikacje *obsługą* dla PWT zablokują dane przedsiębiorstwa z niechronionymi lokalizacjami sieciowymi, aby uniknąć szyfrowania danych osobowych. Program Visual Studio nie jest aplikacją obsługą, więc nie działa w środowiskach z obsługą PWT, chyba że zostanie wykluczony. Wykonaj kroki opisane w tym artykule, aby umożliwić programowi Visual Studio działanie na maszynie z obsługą PWT.

## <a name="configure-vs-as-a-wip-exempt-app"></a>Konfiguracja programu VS jako aplikacja z wykluczeniem PWT

Można wyłączyć program Visual Studio z ograniczeń PWT, ale nadal zezwolić na korzystanie z danych przedsiębiorstwa. Aplikacje z wykluczeniem PWT mogą łączyć się z zasobami w chmurze przedsiębiorstwa przy użyciu adresu IP lub nazwy hosta. Nie zastosowano szyfrowania i aplikacja może uzyskiwać dostęp do plików lokalnych.

Aby wykluczyć program Visual Studio z PWT, postępuj zgodnie z instrukcjami [w celu wykluczenia aplikacji klasycznej](/windows/security/information-protection/windows-information-protection/create-wip-policy-using-intune-azure#exempt-apps-from-a-wip-policy).

## <a name="create-a-wip-exempt-applocker-policy-file"></a>Utwórz plik zasad funkcji AppLocker z wykluczeniem PWT

Ponieważ program Visual Studio zawiera wiele plików binarnych, [Utwórz plik zasad funkcji AppLocker z wykluczeniem PWT](/windows/security/threat-protection/windows-defender-application-control/applocker/run-the-automatically-generate-rules-wizard). Funkcja AppLocker umożliwia automatyczne generowanie reguł dla wszystkich plików w folderze.

## <a name="add-appcompat-to-the-enterprise-cloud-resource-policy"></a>Dodawanie AppCompat do zasad zasobów w chmurze przedsiębiorstwa

Aby określić, gdzie program Visual Studio może uzyskać dostęp do danych przedsiębiorstwa w sieci, wykonaj następujące [kroki, aby określić, gdzie chronione aplikacje mogą znajdować i wysyłać dane przedsiębiorstwa](/windows/security/information-protection/windows-information-protection/create-wip-policy-using-intune-azure#choose-where-apps-can-access-enterprise-data). Aby uniemożliwić systemowi Windows blokowanie połączeń z zasobami w chmurze za pośrednictwem adresu IP, należy dodać do \* Ustawienia/AppCompat \* /ciąg.

## <a name="see-also"></a>Zobacz także

- [Zachowanie aplikacji przy użyciu PWT](/windows/security/information-protection/windows-information-protection/app-behavior-with-wip)
