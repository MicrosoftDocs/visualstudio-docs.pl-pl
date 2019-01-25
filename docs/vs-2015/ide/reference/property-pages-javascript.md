---
title: Strony właściwości, JavaScript | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- javascript.project.property.debugging.debuggertype
- javascript.project.property.debugging.requireauthentication
- javascript.project.property.outputpath
- javascript.project.property.debugging.launchapplication
- javascript.project.property.defaultlanguage
- javascript.project.property.debugging.machinename
- javascript.project.property.debugging.allowlocalnetworkloopback
ms.assetid: a05ab01f-3d5d-4675-a845-eab51807d3a3
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 2ae8687a63f4f49a84a67a2c504ee5bf11769128
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54768145"
---
# <a name="property-pages-javascript"></a>Strony właściwości, JavaScript
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
**Stron właściwości**zapewnia dostęp do ustawień projektu. Można użyć stron, które pojawiają się w **stron właściwości** można zmienić właściwości projektu.  
  
 Aby uzyskać dostęp do właściwości projektu, wybierz węzeł projektu w **Eksploratora rozwiązań**. Na **projektu** menu, kliknij przycisk **właściwości**.  
  
 [!INCLUDE[note_settings_general](../../includes/note-settings-general-md.md)]  
  
 Następujące strony i opcje są wyświetlane w **stron właściwości**.  
  
## <a name="configuration-and-platform-page"></a>Konfiguracja i strona platformy  
 Użyj następujących opcji, aby wybrać konfigurację i platformę do wyświetlenia lub zmodyfikowania.  
  
 **Konfiguracja**  
 Określa ustawienia konfiguracji do wyświetlenia lub zmodyfikowania. Ustawienia są **debugowania** (ustawienie domyślne), **wersji**, **wszystkie konfiguracje**, lub Konfiguracja zdefiniowana przez użytkownika. Aby uzyskać więcej informacji, zobacz [konfiguracji Debug i Release projektu](http://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e).  
  
 **Platforma**  
 Określa ustawienia platformy do wyświetlenia lub zmodyfikowania. Ustawienia są **dowolny Procesor** (domyślne dla [!INCLUDE[win8_appname_long](../../includes/win8-appname-long-md.md)] aplikacji), **x64**, **ARM**, **x86**, lub platforma zdefiniowana przez użytkownika. Aby uzyskać więcej informacji, zobacz [konfiguracji Debug i Release projektu](http://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e).  
  
## <a name="general-page"></a>Strona ogólna  
 Następujące opcje służą do ustawiania właściwości ogólnych projektu.  
  
> [!NOTE]
>  Niektóre opcje są dostępne tylko w aplikacjach Windows Store.  
  
 **Ścieżka wyjściowa**  
 Określa położenie plików wyjściowych dla tej konfiguracji projektu. Ścieżka jest względna; Jeśli wprowadzasz ścieżkę bezwzględną, ścieżka bezwzględna jest zapisywana w projekcie. Domyślna ścieżka to bin\Debug.  
  
 Korzystając z uproszczonych konfiguracjach kompilacji system projektu określa, czy do kompilacji debugowania lub wydania wersji. Po kliknięciu **debugowania**, **Rozpocznij debugowanie** (lub naciśnij klawisz F5) kompilacja jest umieszczany w lokalizacji debugowania bez względu na to **ścieżkę wyjściową** określisz. Jednak **Kompiluj rozwiązanie** polecenie **kompilacji** menu umieszcza go w miejscu określonym przez użytkownika. Aby włączyć zaawansowane konfiguracje kompilacji, na pasku menu wybierz **narzędzia**, **opcje**. W **opcje** okna dialogowego rozwiń **projekty i rozwiązania**, wybierz opcję **ogólne**, a następnie wyczyść **Pokaż zaawansowane konfiguracjekompilacji**pole wyboru. Daje to ręczne sterowanie wszystkimi wartościami konfiguracji i czy jest wbudowana wersja debugowania lub publikacji. Aby uzyskać więcej informacji, zobacz [NIB: Ogólne, projekty i rozwiązania, okno dialogowe Opcje](http://msdn.microsoft.com/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca).  
  
 **Język domyślny**  
 Określa język domyślny dla projektu. Opcja języka wybranego w **zegar, język i Region** w Panelu sterowania określa język preferowany przez użytkownika. Określając język domyślny dla projektu, należy upewnić się, że zasoby określonego domyślnego języka są używane, jeśli język preferowany przez użytkownika nie jest zgodny z zasobami językowymi aplikacji.  
  
## <a name="debug-page"></a>Strona debugowania  
 Aby ustawić właściwości do debugowania zachowania w projekcie, należy użyć następujących opcji.  
  
> [!NOTE]
>  Niektóre opcje są dostępne tylko w aplikacjach Windows Store.  
  
 **Debuger do uruchomienia**  
 Określa host domyślny dla debugera.  
  
- Wybierz **komputera lokalnego** Aby uruchomić aplikację na komputerze-hoście programu Visual Studio. Aby uzyskać więcej informacji, zobacz [uruchamianie aplikacji na komputerze lokalnym](http://go.microsoft.com/fwlink/?LinkId=234912).  
  
- Wybierz **symulator** Aby uruchomić aplikację w symulatorze. Aby uzyskać więcej informacji, zobacz [uruchamiania aplikacji w symulatorze](http://go.microsoft.com/fwlink/?LinkId=234913).  
  
- Wybierz **maszyny zdalnej** Aby uruchomić aplikację na komputerze zdalnym. Aby uzyskać więcej informacji na temat debugowania zdalnego, zobacz [uruchamianie aplikacji na komputerze zdalnym](http://go.microsoft.com/fwlink/?LinkId=234914).  
  
  **Uruchamianie aplikacji**  
  Określa, czy uruchomić aplikację po naciśnięciu klawisza F5 lub kliknij przycisk **debugowania**, **Rozpocznij debugowanie**. Wybierz **tak** do uruchamiania aplikacji; w przeciwnym razie wybierz **nie**. Jeśli wybierzesz **nie**, nadal można debugować aplikację, jeśli używasz innej metody jej uruchomienia.  
  
  **Typ debugera**  
  Określa typy kodu do debugowania. Wybierz **tylko skrypt** do debugowania kodu JavaScript. Wybierz **tylko zarządzane** do debugowania kodu, który jest zarządzany przez środowisko uruchomieniowe języka wspólnego. Wybierz **tylko natywny** do debugowania kodu C++. Wybierz **natywny ze skryptem** debugowania C++ i JavaScript. Wybierz **mieszany (zarządzany i natywny)** do debugowania zarządzanego, jak i kodu w języku C++.  
  
  **Zezwalaj na sprzężenie zwrotne sieci lokalnej**  
  Określa, czy adres IP sprzężenia zwrotnego jest dostęp do testowania aplikacji. Wybierz **tak** Aby zezwolić na użycie adresu sprzężenia zwrotnego Jeśli aplikacja klienta znajduje się na tym samym komputerze, gdzie aplikacja serwera jest uruchomiona; w przeciwnym razie, wybierz **nie**. Ta właściwość jest dostępna tylko wtedy, gdy **debuger do uruchomienia** właściwość jest ustawiona na **maszyny zdalnej**.  
  
  **Nazwa maszyny**  
  Określa nazwę komputera zdalnego hostującego debuger. Ta właściwość jest dostępna tylko wtedy, gdy **debuger do uruchomienia** ustawiono **maszyny zdalnej**.  
  
  **Wymagaj uwierzytelniania**  
  Określa, czy komputer zdalny wymaga uwierzytelniania. Ta właściwość jest dostępna tylko wtedy, gdy **debuger do uruchomienia** ustawiono **maszyny zdalnej**.
