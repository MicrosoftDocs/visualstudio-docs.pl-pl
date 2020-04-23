---
title: 'Jak: Określanie alternatywnej lokalizacji aktualizacji wdrożenia | Dokumenty firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, updates
- deployment update, alternative locations
ms.assetid: 7faacd35-2638-492d-80f6-6b57e5f820de
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8b6388833e6574fc1d631d391fa7b67d5f0a3372
ms.sourcegitcommit: c1339f64fbeee6f17bf80fedea81afc8dac40dc0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "82037223"
---
# <a name="how-to-specify-an-alternate-location-for-deployment-updates"></a>Porady: określanie alternatywnej lokalizacji aktualizacji wdrażania
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Aplikację można zainstalować początkowo z dysku CD lub udziału plików, ale aplikacja musi sprawdzać, czy są okresowe aktualizacje w sieci Web. Można określić alternatywną lokalizację aktualizacji w manifeście wdrożenia, dzięki czemu aplikacja może zaktualizować się z sieci Web po jej początkowej instalacji.  
  
> [!NOTE]
> Aplikacja musi być skonfigurowana do instalacji lokalnie, aby korzystać z tej funkcji. Aby uzyskać więcej informacji, zobacz [Przewodnik: Ręczne wdrażanie aplikacji ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Ponadto po zainstalowaniu [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikacji z sieci ustawienie alternatywnej [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] lokalizacji powoduje użycie tej lokalizacji zarówno dla instalacji początkowej, jak i wszystkich kolejnych aktualizacji. Jeśli aplikacja zostanie zainstalowana lokalnie (na przykład z dysku CD), początkowa instalacja jest wykonywana przy użyciu oryginalnego nośnika, a wszystkie kolejne aktualizacje będą używać lokalizacji alternatywnej.  
  
### <a name="specifying-an-alternate-location-for-updates-by-using-mageuiexe-windows-forms-based-utility"></a>Określanie alternatywnej lokalizacji aktualizacji przy użyciu programu MageUI.exe (narzędzie oparte na formularzach systemu Windows)  
  
1. Otwórz wiersz polecenia programu .NET Framework i wpisz:  
  
     **Mageui.exe**  
  
2. W menu **Plik** wybierz polecenie **Otwórz,** aby otworzyć manifest wdrażania aplikacji.  
  
3. Wybierz kartę **Opcje wdrażania.**  
  
4. W polu tekstowym o nazwie **Lokalizacja uruchamiania**wprowadź adres URL do katalogu, który będzie zawierał manifest wdrażania aktualizacji aplikacji.  
  
5. Zapisz manifest wdrożenia.  
  
### <a name="specifying-an-alternate-location-for-updates-by-using-mageexe"></a>Określanie alternatywnej lokalizacji aktualizacji przy użyciu programu Mage.exe  
  
1. Otwórz wiersz polecenia programu .NET Framework.  
  
2. Ustaw lokalizację aktualizacji za pomocą następującego polecenia. W tym przykładzie **HelloWorld.exe.application** jest [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] ścieżką do manifestu aplikacji, `http://adatum.com/Update/Path` który zawsze [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] ma rozszerzenie .application i jest adresem URL, który będzie sprawdzał dostępność aktualizacji aplikacji.  
  
     **Mag -Update HelloWorld.exe.application -ProviderUrl\/http: /adatum.com/Update/Path**  
  
3. Zapisz plik.  
  
    > [!NOTE]
    > Teraz musisz ponownie podpisać plik za pomocą mage.exe. Aby uzyskać więcej informacji, zobacz [Przewodnik: Ręczne wdrażanie aplikacji ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Jeśli aplikacja zostanie zainstalowana z nośnika offline, takiego jak [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] dysk CD, a `<deploymentProvider>` komputer jest w trybie online, najpierw sprawdza adres URL określony przez tag w manifeście wdrożenia, aby ustalić, czy lokalizacja aktualizacji zawiera nowszą wersję aplikacji. Jeśli tak, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] instaluje aplikację bezpośrednio stamtąd, zamiast z katalogu instalacji początkowej, a wspólny czas wykonywania języka (CLR) określa poziom zaufania aplikacji przy użyciu `<deploymentProvider>`. Jeśli komputer jest w `<deploymentProvider>` trybie offline [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] lub jest nieosiągalny, instaluje się z dysku CD, a program CLR udziela zaufania na podstawie punktu instalacji; w przypadku instalacji dysku CD oznacza to, że aplikacja otrzymuje pełne zaufanie. Wszystkie kolejne aktualizacje odziedziczą ten poziom zaufania.  
  
 Wszystkie [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikacje, które używają `<deploymentProvider>` należy jawnie zadeklarować uprawnienia, których potrzebują w ich manifestu aplikacji, tak aby aplikacja nie otrzymuje różnych poziomów zaufania na różnych komputerach.  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik: Ręczne wdrażanie aplikacji ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)   
 [Manifest wdrażania ClickOnce](../deployment/clickonce-deployment-manifest.md)   
 [Zabezpieczanie aplikacji ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Wybieranie strategii aktualizacji ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)
