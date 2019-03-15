---
title: Podręcznik administratora programu Visual Studio
titleSuffix: ''
description: Dowiedz się więcej o sposobie wdrażania programu Visual Studio w środowisku przedsiębiorstwa.
ms.date: 05/29/2018
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- network installation, Visual Studio
- administrator guide, Visual Studio
- installing Visual Studio, administrator guide
ms.assetid: 4af353f5-6cfd-4ebe-bcfb-f42306e451a0
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b30a104afcbadc9397cc5c7bd79fa746b0e69a9f
ms.sourcegitcommit: 4ffb7be5384ad566ce46538032bf8561754c61a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2019
ms.locfileid: "57983822"
---
# <a name="visual-studio-administrator-guide"></a>Podręcznik administratora programu Visual Studio

W środowiskach przedsiębiorstw jest typowe dla administratorów systemu wdrożyć instalacje do użytkowników końcowych z udziału sieciowego lub za pomocą oprogramowania do zarządzania systemami. Zaprojektowaliśmy się aparat Instalatora programu Visual Studio do obsługi wdrożenia w przedsiębiorstwie, pozwalając administratorom systemów możliwość tworzenia lokalizacji instalacji sieciowej, można wstępnie skonfigurować domyślne ustawienia instalacji, aby wdrożyć kluczy produktów podczas procesu instalacji i do zarządzania aktualizacjami produktu po pomyślne wdrożenie. Ten Przewodnik administratora wskazówki oparte na scenariuszach dotyczące wdrażania w przedsiębiorstwie w środowiskach sieciowych.

## <a name="deploy-visual-studio-in-an-enterprise-environment"></a>Wdrażanie programu Visual Studio w środowisku przedsiębiorstwa

Visual Studio można wdrożyć na klienckich stacjach roboczych, tak długo, jak długo każdy komputer docelowy spełnia [minimalne wymagania dotyczące instalacji](/visualstudio/productinfo/vs2017-system-requirements-vs). Czy jest wdrażany za pomocą oprogramowania, takiego jak System Center lub pliku wsadowego, zazwyczaj należy przejść przez następujące kroki:

1. [Utwórz udział sieciowy, który zawiera pliki produktu Visual Studio](create-a-network-installation-of-visual-studio.md) do lokalizacji sieciowej.

2. [Wybieranie obciążenia i składniki](workload-and-component-ids.md) chcesz zainstalować.

3. [Utwórz plik odpowiedzi](automated-installation-with-response-file.md) zawierający domyślne opcje instalacji. Lub też [kompilacji skrypt instalacyjny](use-command-line-parameters-to-install-visual-studio.md) używający parametry wiersza polecenia do sterowania instalacji.

4. Opcjonalnie [Zastosuj klucz produktu licencji zbiorczej](automatically-apply-product-keys-when-deploying-visual-studio.md) jako część instalacji skryptu, aby użytkownicy nie musieli aktywować oprogramowania oddzielnie.

5. Aktualizowanie układu sieci, aby [kontrolowania, kiedy aktualizacje produktu są dostarczane do użytkowników końcowych](controlling-updates-to-visual-studio-deployments.md).

6. Opcjonalnie można ustawić klucze rejestru, [kontrolować, co jest buforowana na klienckich stacjach roboczych](set-defaults-for-enterprise-deployments.md).

7. Użyj wybranej technologii wdrożenia można wykonać skryptu wygenerowane w poprzednich krokach na docelowych stacjach roboczych dla deweloperów.

8. [Odśwież lokalizacji sieciowej, z najnowszymi aktualizacjami](update-a-network-installation-of-visual-studio.md) do programu Visual Studio za pomocą polecenia używane w kroku 1 w regularnych odstępach czasu, aby dodać zaktualizowane składniki.

> [!IMPORTANT]
> Należy pamiętać, że urządzenia z sieci udziału "zapamiętają" w lokalizacji źródłowej pochodzą z. Oznacza to, naprawy maszyny klienta może być konieczne powrócić do udziału sieciowego, który pierwotnie zainstalowany klient z. Wybierz lokalizację sieci dokładnie tak, aby powoduje wyrównanie z okresem istnienia, których oczekujesz, że aby klienci programu Visual Studio w organizacji.

## <a name="use-visual-studio-tools"></a>Za pomocą narzędzi Visual Studio

Mamy kilka narzędzi, które ułatwiają [wykrywania wystąpień i zarządzanie nimi zainstalowanego programu Visual Studio](tools-for-managing-visual-studio-instances.md) na maszynach klienckich.

> [!TIP]
> Oprócz dokumentacji w przewodniku administratora, jest dobrym źródłem informacji na temat instalacji programu Visual Studio [Visual Studio Instalator archiwa](https://devblogs.microsoft.com/setup/tag/vs2017/).

## <a name="specify-customer-feedback-settings"></a>Określanie ustawień opinii klienta

Domyślnie instalacja programu Visual Studio umożliwia opinii klientów. Po włączeniu zasad grupy, można skonfigurować programu Visual Studio, aby wyłączyć opinie klientów na poszczególnych komputerach. Aby to zrobić, należy ustawić zasady opartych na rejestrze dla następującego klucza:

**HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\VisualStudio\SQM**

Wpis = **OptIn**

Wartość = (DWORD)
* **0** jest wyłączony
* **1** jest zgoda

Aby uzyskać więcej informacji na temat ustawień opinii klienta, zobacz [programu poprawy jakości obsługi klienta programu Visual Studio](../ide/visual-studio-experience-improvement-program.md) strony.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Zobacz także

* [Instalowanie programu Visual Studio](install-visual-studio.md)
* [Korzystanie z parametrów wiersza polecenia do zainstalowania programu Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
  * [Przykładowe parametry wiersza polecenia](command-line-parameter-examples.md)
  * [Odwołanie do obciążenia i identyfikator składnika](workload-and-component-ids.md)
* [Utwórz na podstawie sieci instalację programu Visual Studio](create-a-network-installation-of-visual-studio.md)
  * [Instalowanie certyfikatów wymaganych do instalacji w trybie offline programu Visual Studio](install-certificates-for-visual-studio-offline.md)
* [Automatyzacja Visual Studio przy użyciu pliku odpowiedzi](automated-installation-with-response-file.md)
* [Automatyczne stosowanie kluczy produktów podczas wdrażania programu Visual Studio](automatically-apply-product-keys-when-deploying-visual-studio.md)
* [Ustawianie wartości domyślnych dla wdrożeń programu Visual Studio w przedsiębiorstwie](set-defaults-for-enterprise-deployments.md)
* [Wyłączanie lub przenoszenie pamięci podręcznej pakietów](disable-or-move-the-package-cache.md)
* [Aktualizowanie instalacji opartej na sieci, programu Visual Studio](update-a-network-installation-of-visual-studio.md)
* [Sterowanie aktualizacjami na potrzeby wdrożeń programu Visual Studio](controlling-updates-to-visual-studio-deployments.md)
* [Narzędzia do wykrywania wystąpień programu Visual Studio i zarządzania nimi](tools-for-managing-visual-studio-instances.md)
