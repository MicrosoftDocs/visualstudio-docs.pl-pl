---
title: Program Visual Studio na urządzeniach z systemem ARM
description: Zalecenia dotyczące korzystania z programu Visual Studio na urządzeniach z procesorami opartymi na architekturze ARM.
ms.date: 09/10/2020
ms.topic: conceptual
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 31fb209a3f19c052c19e98691b8643bb098887ee
ms.sourcegitcommit: 6d88913a8b5a9e5eda01d3f95205b4d138f440f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/13/2021
ms.locfileid: "107295809"
---
# <a name="visual-studio-on-arm-powered-devices"></a>Program Visual Studio na urządzeniach opartych na architekturze ARM

> [!IMPORTANT]
> Program Visual Studio jest obsługiwany tylko na urządzeniach z procesorem x86 lub AMD64/x64.

Program Visual Studio jest zbudowany na potrzeby procesorów opartych na architekturze x86 i nie ma wersji programu Visual Studio dla procesorów opartych na usłudze ARM. System Windows udostępnia jednak [emulację architektury x86 na ARM](https://www.docs.microsoft.com/windows/uwp/porting/apps-on-arm-x86-emulation), którą można uruchomić w programie Visual Studio. Uruchamianie programu Visual Studio na procesorze ARM za pośrednictwem emulacji x86 poważnie ogranicza wydajność programu Visual Studio, a kilka funkcji programu Visual Studio nie jest przeznaczonych do pracy w tym scenariuszu. W związku z tym nie zalecamy uruchamiania programu Visual Studio na urządzeniach korzystających z procesorów opartych na architekturze ARM, a zamiast tego zaleca się zdalnie kierowanym urządzeniom ARM.

## <a name="remote-targeting-arm-devices"></a>Zdalne kierowanie urządzeń ARM
Aby uzyskać najlepsze doświadczenia, zalecamy korzystanie z programu Visual Studio na osobnym komputerze z procesorem x86, a następnie korzystanie z funkcji zdalnego wdrażania i debugowania w programie Visual Studio w celu kierowania urządzeniem opartym na architekturze ARM. Aby debugować aplikacje uniwersalne systemu Windows, które są już zainstalowane na urządzeniu, zobacz dokumentację dotyczącą [debugowania zainstalowanego pakietu aplikacji](../debugger/debug-installed-app-package.md) . Aby wdrożyć nową aplikację, zobacz [Uruchamianie aplikacji ze sklepu Windows remotley](../debugger/run-windows-store-apps-on-a-remote-machine.md). Dla wszystkich innych typów aplikacji zapoznaj się z dokumentacją [zdalnego debugowania](../debugger/remote-debugging.md) .

## <a name="tips-for-running-visual-studio-on-arm-devices"></a>Porady dotyczące uruchamiania programu Visual Studio na urządzeniach ARM

### <a name="use-only-when-needed"></a>Używaj tylko w razie konieczności
Zoptymalizuj czas, używając programu Visual Studio tylko w razie potrzeby dla pracy specyficznej dla ARM. Wydajność na dowolnym urządzeniu opartym na usłudze ARM jest niska i prawdopodobnie nie będzie można jej używać do zwykłych potrzeb.

### <a name="install-time"></a>Godzina instalacji
Zaplanuj, aby program Visual Studio mógł dłużej instalować i oczekiwać na jego wstrzymanie przez okres czasu lub wymagać ponownego uruchomienia.
 
### <a name="remote-tools"></a>Zdalne narzędzia
Aby debugować aplikację uruchomioną na urządzeniu zdalnym, musisz [pobrać i zainstalować narzędzia Remote Tools](../debugger/remote-debugging.md#download-and-install-the-remote-tools) for ARM.

### <a name="start-debugging-f5"></a>Rozpocznij debugowanie (F5)
Nie wszystkie projekty programu Visual Studio są skonfigurowane do uruchamiania projektów lokalnie po rozpoczęciu debugowania (**F5**) z poziomu urządzenia ARM. Może być konieczne skonfigurowanie programu Visual Studio na potrzeby debugowania zdalnego, nawet jeśli aplikacja działa lokalnie. Aby uzyskać więcej informacji, zobacz [debugowanie zdalne](../debugger/remote-debugging.md).

## <a name="we-need-your-help"></a>Potrzebujemy Twojej pomocy!
Jeśli chcesz, aby program Visual Studio mógł działać natywnie na urządzeniach ARM, chcielibyśmy poznać scenariusze i pomoc techniczną. Możesz skontaktować się z nami, publikując ją w [społeczności deweloperów](https://developercommunity.visualstudio.com/idea/1161018/native-arm-support-for-visual-studio.html).
