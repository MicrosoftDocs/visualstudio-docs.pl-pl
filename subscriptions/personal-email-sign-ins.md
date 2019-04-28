---
title: Osobistych adresów E-mail wyświetlany w witrynie VLSC
author: evanwindom
ms.author: jaunger
manager: evelynp
ms.date: 01/23/2018
ms.topic: conceptual
description: Subskrypcje programu Visual Studio — dlaczego widzę Hotmail lub Gmail adresy moich subskrybentów?
searchscope: VS Subscription
ms.openlocfilehash: 0ba4029fcec0c8d35a58def14ab38afbb79e2fee
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62539459"
---
# <a name="visual-studio-subscriptions--why-am-i-seeing-hotmail-or-gmail-addresses-for-my-subscribers"></a>Subskrypcje programu Visual Studio — dlaczego widzę adresy Hotmail lub Gmail moich subskrybentów?

Jak firmy migracji z woluminu licencjonowania Service Center (VLSC) do nowego programu Visual Studio [portal administratora subskrypcji](https://manage.visualstudio.com), Administratorzy mogą być zaskoczeniem, się okazać, że "Sign in adres E-mail" dla niektórych subskrybentów Pokazuje 3 strony adres e-mail, takich jak Hotmail, Gmail lub Yahoo.  Aby uzyskać więcej informacji, zapoznaj się z [ten film wideo](https://www.youtube.com/watch?v=1op-i1zEMfY&t=0s&list=PLReL099Y5nRfDyvvwzNDBaZe7qTxmuM2T&index=6).

## <a name="cause"></a>Przyczyna

W tym scenariuszu występuje z powodu procesów logowania, które zostały skojarzone z ze starszej wersji środowiska dla subskrybentów MSDN. Użytkownicy, zostały poddane migracji z woluminu licencji Service Center (VLSC) do nowego portalu bez modyfikacji. Administratorzy mogą nie zostać pamiętać, że użytkownicy tej pory było używane konta osobiste na dostęp do korzyści z subskrypcji. Przed migracji dla subskrybentów programu Visual Studio, które zostały wykonane na 2016, istniały dwie akcje wymagane, aby pomyślnie korzystać z subskrypcji programu Visual Studio:
1. Administrator "przypisane" subskrypcji do poszczególnych subskrybentów przy użyciu ich służbowego adresu e-mail.
2. Subskrybent "aktywowano" subskrypcji.

Podczas procesu aktywacji subskrybenta: Konto Microsoft (MSA) była wymagana do logowania. Jeśli subskrybent nie podejmuje próby wykonania swojego konta służbowego (np. tasha@contoso.com) wiadomość MSA, ich można utworzyć nowego konta Microsoft lub wykorzystać istniejącą grupę. Pozwoliło to odnotować "Sign in adresu E-mail" jest inny niż "Przypisane do adresów E-mail".

> [!NOTE]
> Nowe środowisko dla subskrybentów na [ https://my.visualstudio.com ](https://my.visualstudio.com?wt.mc_id=o~msft~docs) obsługuje zarówno służbowe, jak i konto Microsoft (MAA) typów tożsamości.

Na koniec ponieważ migracja administrator trwa dane z witryny VLSC dotyczące "Logowanie w adresie E-mail subskrybenta" do wypełnienia nowego środowiska zarządzania subskrybenta, zmigrowanych niedawno Administratorzy może zostać wyświetlony te wcześniej niezauważona kont osobistych, ze względu na zmiany interfejsu użytkownika, które uwidocznić te informacje.

## <a name="solution"></a>Rozwiązanie

Aby rozwiązać ten problem, należy edytować informacje subskrybenta do zaktualizowania ich adresy e-mail logowania.  Można wprowadzić zmiany dla poszczególnych subskrybentów lub zbiorczo. Aby uzyskać pełne informacje, odwiedź [edytowanie subskrypcji](edit-license.md).

Po zaktualizowaniu adresy e-mail subskrybentów można powiadamiać o tym, że zmienił się informacjami logowania.  Również otrzymają wiadomość e-mail przy użyciu zaktualizowanych informacji.