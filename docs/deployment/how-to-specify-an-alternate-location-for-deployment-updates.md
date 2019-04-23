---
title: 'Instrukcje: Określanie alternatywnej lokalizacji aktualizacji wdrażania | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, updates
- deployment update, alternative locations
ms.assetid: 7faacd35-2638-492d-80f6-6b57e5f820de
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 14a1c072cb8415e8e0a20615c0c963e683f48b56
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60041357"
---
# <a name="how-to-specify-an-alternate-location-for-deployment-updates"></a>Instrukcje: Określanie alternatywnej lokalizacji aktualizacji wdrażania
Można zainstalować usługi [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacja początkowo z dysku CD lub udział plików, ale aplikacja musi sprawdzić okresowe aktualizacje w sieci Web. Tak, aby aplikacja może automatycznie zaktualizowana z sieci Web po jego wstępnej instalacji, można określić alternatywną lokalizację aktualizacji w manifeście wdrożenia.

> [!NOTE]
>  Twoja aplikacja musi być skonfigurowana do zainstalowania lokalnie, aby użyć tej funkcji. Aby uzyskać więcej informacji, zobacz [instruktażu: Ręczne wdrażanie aplikacji ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Ponadto, jeśli zainstalujesz [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] na ustawienie lokalizacji alternatywnej powoduje, że sieci [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] można użyć tej lokalizacji dla początkowej instalacji i wszystkich kolejnych aktualizacji. Po zainstalowaniu aplikacji w środowisku lokalnym (na przykład z dysku CD), początkowej instalacji odbywa się przy użyciu oryginalnego nośnika, a wszystkie kolejne aktualizacje użyje lokalizacji alternatywnej.

### <a name="specify-an-alternate-location-for-updates-by-using-mageuiexe-windows-forms-based-utility"></a>Określanie alternatywnej lokalizacji aktualizacji za pomocą MageUI.exe (narzędzie oparte na formularzach Windows)

1. Otwórz wiersz polecenia w programie .NET Framework i wpisz:

     **mageui.exe**

2. Na **pliku** menu, wybierz **Otwórz** na otwarcie manifestu wdrażania aplikacji.

3. Wybierz **opcje wdrażania** kartę.

4. W polu tekstowym o nazwie **Uruchom lokalizacji**, wprowadź adres URL do katalogu, który będzie zawierać manifest wdrażania aktualizacji aplikacji.

5. Zapisywanie pliku manifestu wdrożenia.

### <a name="specify-an-alternate-location-for-updates-by-using-mageexe"></a>Określanie alternatywnej lokalizacji aktualizacji za pomocą Mage.exe

1. Otwórz wiersz polecenia .NET Framework.

2. Ustaw lokalizację aktualizacji, używając następującego polecenia. W tym przykładzie *HelloWorld.exe.application* jest ścieżką do Twojego [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifest aplikacji, która zawsze ma rozszerzenie .application, i *<http://adatum.com/Update/Path>* jest adres URL tego [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] będzie szukać aktualizacji aplikacji.

    **Mage -Update HelloWorld.exe.application -ProviderUrl http://adatum.com/Update/Path**

3. Zapisz plik.

   > [!NOTE]
   >  Teraz należy ponownie podpisać plik za pomocą *Mage.exe*. Aby uzyskać więcej informacji, zobacz [instruktażu: Ręczne wdrażanie aplikacji ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).

## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework
 Jeśli instalowanie aplikacji w trybie offline średnie, takich jak dysk CD, a komputer jest w trybie online [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] najpierw sprawdza ją pod adres URL określony przez `<deploymentProvider>` tag w manifeście wdrożenia, aby ustalić, czy lokalizacji aktualizacji zawiera nowszą wersję aplikacja. Jeśli tak jest, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] instaluje aplikację bezpośrednio stamtąd, a nie z katalogu instalacji początkowej i środowisko uruchomieniowe języka wspólnego (CLR) określa zaufania aplikacji przy użyciu na poziomie `<deploymentProvider>`. Jeśli komputer jest w trybie offline lub `<deploymentProvider>` jest nieosiągalny, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] instalacji z dysku CD, a środowisko CLR przyznaje zaufania, w oparciu o punkt instalacji; w przypadku instalacji z dysku CD, oznacza to, Twoja aplikacja otrzyma pełnego zaufania. Wszystkie kolejne aktualizacje będą dziedziczyć ten poziom zaufania.

 Wszystkie [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacje, które używają `<deploymentProvider>` powinny jawnie deklarować uprawnień potrzebnych w manifeście aplikacji tak, aby aplikacja nie otrzyma różne poziomy zaufania na różnych komputerach.

## <a name="see-also"></a>Zobacz także
- [Przewodnik: Ręczne wdrażanie aplikacji ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)
- [Manifest wdrażania ClickOnce](../deployment/clickonce-deployment-manifest.md)
- [Zabezpieczanie aplikacji ClickOnce](../deployment/securing-clickonce-applications.md)
- [Wybieranie strategii aktualizacji ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)