---
title: Strona zabezpieczeń, Projektant projektu
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesSecurity
- vb.XBAPProjectPropertiesSecurity
helpviewer_keywords:
- Project Designer, Security page
- Security page in Project Designer
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 29723f5e253a2ff6d4f6c35e8ad8d3e09e2393f1
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72748656"
---
# <a name="security-page-project-designer"></a>Strona zabezpieczeń, Projektant projektu

Strona **zabezpieczeń** **projektanta projektu** służy do konfigurowania ustawień zabezpieczeń dostępu kodu dla aplikacji, które są wdrażane przy użyciu wdrażania ClickOnce. Aby uzyskać więcej informacji, zobacz [zabezpieczenia dostępu kodu dla aplikacji ClickOnce](../../deployment/code-access-security-for-clickonce-applications.md).

Aby uzyskać dostęp do strony **zabezpieczenia** , kliknij węzeł projektu w **Eksplorator rozwiązań**, a następnie w menu **projekt** kliknij polecenie **Właściwości**. Gdy zostanie wyświetlony **Projektant projektu** , kliknij kartę **zabezpieczenia** .

## <a name="security-settings"></a>Ustawienia zabezpieczeń

 **Włącz ustawienia zabezpieczeń ClickOnce**

Określa, czy ustawienia zabezpieczeń są włączone w czasie projektowania. Po wyczyszczeniu tej opcji wszystkie inne opcje na stronie **zabezpieczenia** są niedostępne.

> [!NOTE]
> W przypadku publikowania aplikacji za pomocą kreatora **publikacji** ta opcja jest włączana automatycznie.

Po wybraniu tej opcji istnieje możliwość wybrania jednego z dwóch przycisków radiowych: **jest to aplikacja o pełnej zaufaniu** lub **jest to częściowo zaufana aplikacja**.

Domyślnie w przypadku projektów aplikacji przeglądarki sieci Web WPF ta opcja jest zaznaczona.

Domyślnie dla wszystkich innych typów projektów ta opcja jest wyczyszczona.

 **To jest aplikacja o pełnej relacji zaufania**

W przypadku wybrania tej opcji aplikacja żąda uprawnień pełnego zaufania, gdy zostanie zainstalowana lub uruchomiona na komputerze klienckim. Należy unikać używania pełnego zaufania, jeśli jest to możliwe, ponieważ aplikacja będzie mieć nieograniczony dostęp do zasobów, takich jak system plików i rejestr.

Domyślnie dla projektów aplikacji przeglądarki sieci Web WPF ta opcja jest ustawiona na wartość częściowa relacja zaufania.

Domyślnie dla wszystkich innych typów projektów ta opcja jest ustawiona na pełne zaufanie.

 **To jest częściowo zaufana aplikacja**

W przypadku wybrania tej opcji aplikacja żąda uprawnień częściowej relacji zaufania, gdy zostanie zainstalowana lub uruchomiona na komputerze klienckim. *Częściowe zaufanie* oznacza, że zostaną uruchomione tylko akcje, które są dozwolone w ramach żądanych uprawnień dostępu kodu. Więcej informacji o sposobie konfigurowania uprawnień zabezpieczeń znajduje się w temacie [zabezpieczenia dostępu kodu dla aplikacji ClickOnce](../../deployment/code-access-security-for-clickonce-applications.md).

Ustawienia zabezpieczeń częściowej relacji zaufania można określić przez skonfigurowanie opcji w obszarze **uprawnienia zabezpieczeń ClickOnce** .

## <a name="clickonce-security-permissions"></a>Uprawnienia zabezpieczeń ClickOnce

 **Strefa, z której zostanie zainstalowana aplikacja**

Określa domyślny zestaw uprawnień zabezpieczeń dostępu kodu. Wybierz opcję **Internet** lub **Lokalny intranet** dla ograniczonego zestawu uprawnień lub wybierz **(niestandardowy)** , aby skonfigurować niestandardowy zestaw uprawnień. Jeśli aplikacja zażąda więcej uprawnień niż udzielono ich w strefie, zostanie wyświetlony monit zaufania ClickOnce dla użytkownika końcowego w celu udzielenia dodatkowych uprawnień. Więcej informacji o sposobie konfigurowania uprawnień zabezpieczeń znajduje się w temacie [zabezpieczenia dostępu kodu dla aplikacji ClickOnce](../../deployment/code-access-security-for-clickonce-applications.md).

Domyślnie dla projektów aplikacji przeglądarki sieci Web WPF ta opcja jest ustawiona na **Internet**.

 **Edytuj uprawnienia XML**

Otwiera szablon manifestu aplikacji (App. manifest) w celu skonfigurowania uprawnień dla zestawu uprawnień **(Custom)** .

 **Zaawansowane**

Otwiera [okno dialogowe Zaawansowane ustawienia zabezpieczeń](../../ide/reference/advanced-security-settings-dialog-box.md), które służy do konfigurowania ustawień debugowania aplikacji z ograniczonymi uprawnieniami. Te ustawienia są sprawdzane podczas debugowania, a wyjątki uprawnień wskazują, że aplikacja może potrzebować więcej uprawnień niż określono w strefie.

## <a name="see-also"></a>Zobacz także

- <xref:System.Security.Permissions.WebBrowserPermission>
- <xref:System.Security.Permissions.MediaPermission>
- [Zabezpieczenia dostępu kodu dla aplikacji ClickOnce](../../deployment/code-access-security-for-clickonce-applications.md)
- [Instrukcje: włączenie ustawień zabezpieczeń technologii ClickOnce](../../deployment/how-to-enable-clickonce-security-settings.md)
- [Instrukcje: ustawienie strefy zabezpieczeń dla aplikacji ClickOnce](../../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)
- [Instrukcje: ustawienie uprawnień niestandardowych dla aplikacji ClickOnce](../../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)
- [Instrukcje: debugowanie aplikacji ClickOnce przy użyciu ograniczonych uprawnień](../../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)
- [Wskazówki dotyczące wdrażania i zabezpieczeń ClickOnce](../../deployment/clickonce-security-and-deployment.md)
- [Odwołanie do właściwości projektu](../../ide/reference/project-properties-reference.md)
- [Zaawansowane ustawienia zabezpieczeń, okno dialogowe](../../ide/reference/advanced-security-settings-dialog-box.md)