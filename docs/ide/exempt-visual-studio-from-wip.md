---
title: Zwolnione z ochrony informacji o systemie Windows
ms.date: 06/01/2018
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8b4eb454f641b5bef7273464d605fb194f650790
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75588567"
---
# <a name="configure-visual-studio-as-a-wip-exempt-app"></a>Konfigurowanie programu Visual Studio jako aplikacji zwolnionej z WIP

[Ochrona informacji systemu Windows](/windows/security/information-protection/windows-information-protection/protect-enterprise-data-using-wip) (PWT) pomaga chronić dane przedsiębiorstwa przed wyciekiem za pośrednictwem aplikacji, takich jak poczta e-mail, media społecznościowe i chmura publiczna, które znajdują się poza kontrolą przedsiębiorstwa. PWT pomaga chronić przed przypadkowym wyciekiem danych na urządzeniach należących do przedsiębiorstwa i urządzeniach osobistych, bez konieczności wprowadzania zmian w środowisku lub innych aplikacjach.

Oczekuje się, że *oświecone* aplikacje dla PWT uniemożliwią przesyłanie danych przedsiębiorstwa do niechronionych lokalizacji sieciowych i unikną szyfrowania danych osobowych. Visual Studio nie jest oświeconą aplikacją, więc nie działa w środowiskach obsługujących PWT, chyba że go zwolnić. Wykonaj kroki opisane w tym artykule, aby włączyć program Visual Studio do działania na komputerze z obsługą PWT.

## <a name="configure-vs-as-a-wip-exempt-app"></a>Konfigurowanie usługi VS jako aplikacji zwolnionej z WIP

Program Visual Studio można wyłączyć z ograniczeń PWT, ale nadal zezwalać na używanie danych przedsiębiorstwa. Aplikacje zwolnione z RWPW mogą łączyć się z zasobami chmury przedsiębiorstwa przy użyciu adresu IP lub nazwy hosta. Szyfrowanie nie jest stosowane, a aplikacja może uzyskać dostęp do plików lokalnych.

Aby zwolnić program Visual Studio z PWT, wykonaj [kroki, aby zwolnić aplikację klasyczną](/windows/security/information-protection/windows-information-protection/create-wip-policy-using-intune-azure#exempt-apps-from-a-wip-policy).

## <a name="create-a-wip-exempt-applocker-policy-file"></a>Tworzenie pliku zasad ograniczeń oprogramowania zwolnionego z funkcji PWT

Ponieważ program Visual Studio zawiera wiele plików binarnych, [należy utworzyć plik zasad ograniczeń oprogramowania wyłączony z funkcji WIP](/windows/security/threat-protection/windows-defender-application-control/applocker/run-the-automatically-generate-rules-wizard). Funkcja AppLocker umożliwia automatyczne generowanie reguł dla wszystkich plików w folderze.

## <a name="add-appcompat-to-the-enterprise-cloud-resource-policy"></a>Dodawanie aplikacji Do zasad zasobów w chmurze przedsiębiorstwa

Aby określić, gdzie program Visual Studio może uzyskiwać dostęp do danych przedsiębiorstwa w sieci, wykonaj następujące [kroki, aby określić, gdzie chronione aplikacje mogą znajdować i wysyłać dane przedsiębiorstwa.](/windows/security/information-protection/windows-information-protection/create-wip-policy-using-intune-azure#choose-where-apps-can-access-enterprise-data) Aby zapobiec blokowaniu połączeń przez system Windows z zasobami w\*chmurze\*za pośrednictwem adresu IP, należy dodać / AppCompat / ciąg do ustawienia.

## <a name="see-also"></a>Zobacz też

- [Zachowanie aplikacji z PWT](/windows/security/information-protection/windows-information-protection/app-behavior-with-wip)
