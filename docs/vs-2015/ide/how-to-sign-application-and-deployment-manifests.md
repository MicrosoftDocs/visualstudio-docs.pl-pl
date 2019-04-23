---
title: 'Instrukcje: Podpisywanie aplikacji i manifestów wdrożenia | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- manifests [Visual Studio]
- code signing [Visual Studio], Authenticode
- deployment manifests [Visual Studio]
- signing manifests [Visual Studio]
- application manifests [Visual Studio]
- ClickOnce deployment [Visual Studio], signing assemblies
- key files [Visual Studio]
- assemblies [Visual Studio], signing
ms.assetid: 64173505-8bfb-41cf-a0de-b9075173f3a2
caps.latest.revision: 61
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: ef782929b24d6f5e06c8e64aec53763481c503eb
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60051704"
---
# <a name="how-to-sign-application-and-deployment-manifests"></a>Instrukcje: Podpisywanie aplikacji i manifestów wdrożenia
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Jeśli chcesz opublikować aplikację za pomocą wdrażania ClickOnce, manifestów aplikacji i wdrożenia muszą być podpisane parą kluczy publiczny/prywatny i podpisany przy użyciu technologii Authenticode. Aby podpisać manifesty, przy użyciu certyfikatu z magazynu certyfikatów Windows lub plikiem klucza.  
  
 Aby uzyskać więcej informacji na temat wdrażania ClickOnce zobacz [wdrażania i zabezpieczeń ClickOnce](../deployment/clickonce-security-and-deployment.md).  
  
 Podpisywanie manifestów ClickOnce jest opcjonalne dla aplikacji opartych na .exe. Aby uzyskać więcej informacji zobacz sekcję "Generowanie nieoznaczonych manifestów" w tym dokumencie.  
  
 Aby uzyskać informacje o tworzeniu plików kluczy, zobacz [jak: Tworzenie pary kluczy publiczny prywatny](http://msdn.microsoft.com/library/05026813-f3bd-4d7c-9e0b-fc588eb3d114).  
  
> [!NOTE]
>  [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] obsługuje tylko te kluczowe pliki wymiany informacji osobistych (PFX), które mają rozszerzenie .pfx. Jednak można wybrać inne typy certyfikatów z magazynu certyfikatów Windows bieżącego użytkownika, klikając **wybierać Store** na **podpisywanie** strony właściwości projektu.  
  
### <a name="to-sign-application-and-deployment-manifests-using-a-certificate"></a>Aby oznaczyć aplikację i wdrażania manifestów za pomocą certyfikatu  
  
1. Przejdź do okna właściwości projektu (kliknij prawym przyciskiem myszy węzeł projektu w **Eksploratora rozwiązań** i wybierz **właściwości**, lub typu **właściwości projektu** w **Szybkie uruchamianie** okna, naciśnij klawisze ALT + ENTER w **Eksploratora rozwiązań** okno). Na **podpisywanie** zaznacz **Podpisz manifesty ClickOnce** pole wyboru.  
  
2. Kliknij przycisk **wybierać Store** przycisku.  
  
     **Wybierz certyfikat** okno dialogowe pojawia się i wyświetla zawartość w magazynie certyfikatów Windows.  
  
    > [!TIP]
    >  Jeśli klikniesz **kliknij tutaj, aby wyświetlić właściwości certyfikatu**, **szczegóły certyfikatu** pojawi się okno dialogowe. To okno dialogowe zawiera szczegółowe informacje o certyfikacie i zawiera dodatkowe opcje. Możesz kliknąć pozycję **certyfikaty** Aby wyświetlić dodatkowe informacje pomocy.  
  
3. Wybierz certyfikat, którego chcesz użyć do podpisania manifestów.  
  
4. Ponadto można określić adres serwera znacznika czasowego w **adres URL serwera znacznika czasowego** pola tekstowego. Jest to serwer zapewniający znacznik czasu określający kiedy manifest została podpisana.  
  
### <a name="to-sign-application-and-deployment-manifests-using-an-existing-key-file"></a>Aby oznaczyć aplikację i wdrażania manifestów za pomocą istniejącego pliku kluczowego  
  
1. Na **podpisywanie** wybierz opcję **Podpisz manifesty ClickOnce** pole wyboru.  
  
2. Kliknij przycisk **wybierz z pliku** przycisku.  
  
     **Wybierz plik** pojawi się okno dialogowe.  
  
3. W **okno dialogowe Wybierz plik** przejdź do lokalizacji pliku klucza (.pfx), który chcesz użyć, a następnie kliknij **Otwórz**.  
  
    > [!NOTE]
    >  Ta opcja obsługuje tylko pliki, które mają rozszerzenie .pfx. Jeśli masz plik klucza lub certyfikat w innym formatu, zapisz go w magazynie certyfikatów Windows i wybierz certyfikat jest opisane w poprzedniej procedurze. Wybrany cel certyfikatu powinien zawierać oznaczanie kodu.  
  
     **Wprowadź hasło do otwarcia pliku** pojawi się okno dialogowe. (Plik PFX jest już przechowywany w magazynie certyfikatów Windows lub nie jest chroniony hasłem, możesz nie jest monitowany o podanie hasła.)  
  
4. Wprowadź hasło, aby uzyskać dostęp do pliku klucza, a następnie naciśnij klawisz ENTER.  
  
### <a name="to-sign-application-and-deployment-manifests-using-a-test-certificate"></a>Aby oznaczyć aplikację i wdrażania manifestów za pomocą certyfikatu testu  
  
1. Na **podpisywanie** wybierz opcję **Podpisz manifesty ClickOnce** pole wyboru.  
  
2. Aby utworzyć nowy certyfikat do testowania, kliknij przycisk **Utwórz certyfikat testu** przycisku.  
  
3. W **Utwórz certyfikat testu** okna dialogowego wprowadź hasło, aby zabezpieczyć swój certyfikat testowy.  
  
## <a name="generating-unsigned-manifests"></a>Trwa generowanie nieoznaczonych manifestów  
 Podpisywanie manifestów ClickOnce jest opcjonalne dla aplikacji opartych na .exe. Poniższe procedury pokazują, jak generować niepodpisane manifesty ClickOnce.  
  
> [!IMPORTANT]
>  Nieoznaczone manifesty mogą uprościć rozwój i testowanie aplikacji. Jednak nieoznaczone manifesty stanowią znaczne zagrożenie dla bezpieczeństwa w środowisku produkcyjnym. Rozważ tylko użycie nieoznaczonych manifestów, jeśli aplikacja ClickOnce działa na komputerach w sieci intranet, która jest całkowicie odizolowana od Internetu lub innych źródeł złośliwego kodu.  
  
 Domyślnie ClickOnce automatycznie generuje podpisane manifesty, chyba że jeden lub więcej plików są szczególnie wyłączone z wygenerowanym mieszania. Innymi słowy, publikowanie aplikacji prowadzi do podpisanych manifestów, jeśli wszystkie pliki są uwzględnione w funkcji mieszającej, nawet wtedy, gdy **Podpisz manifesty ClickOnce** pole wyboru jest wyczyszczone.  
  
#### <a name="to-generate-unsigned-manifests-and-include-all-files-in-the-generated-hash"></a>Aby wygenerować manifest i Dołącz wszystkie pliki do wygenerowanego skrótu  
  
1. Aby wygenerować nieoznaczony manifest, który zawiera wszystkie pliki w skrócie, musisz najpierw opublikować aplikację razem z podpisanych manifestów. W związku z tym najpierw Oznacz manifest ClickOnce wypełniając jedną z poprzednich procedur, a następnie Opublikuj aplikację.  
  
2. Na **podpisywanie** strony, wyczyść **Podpisz manifesty ClickOnce** pole wyboru.  
  
3. Resetuj wersję publikacji, tak że tylko jedna wersja aplikacji jest dostępna. Domyślnie program Visual Studio automatycznie zwiększa numer wersji publikowanej wersji za każdym razem, gdy spróbujesz opublikować aplikację. Aby uzyskać więcej informacji, zobacz [jak: ClickOnce ustawienie wersji publikacji](../deployment/how-to-set-the-clickonce-publish-version.md).  
  
4. Opublikuj aplikację.  
  
#### <a name="to-generate-unsigned-manifests-and-exclude-one-or-more-files-from-the-generated-hash"></a>Aby wygenerować manifest i wykluczyć jeden lub więcej plików z wygenerowanego skrótu  
  
1. Na **podpisywanie** strony, wyczyść **Podpisz manifesty ClickOnce** pole wyboru.  
  
2. Otwórz **pliki aplikacji** okno dialogowe i ustaw **skrótu** do **wykluczyć** dla plików, które chcesz wykluczyć z wygenerowanego mieszania.  
  
    > [!NOTE]
    >  Wykluczanie pliku ze skrótu konfiguruje funkcję ClickOnce, aby wyłączyć automatyczne oznaczanie manifestów, więc nie trzeba najpierw publikować oznaczonych manifestów jak pokazano w poprzedniej procedurze.  
  
3. Opublikuj aplikację.  
  
## <a name="see-also"></a>Zobacz też  
 [Zestawy o silnych nazwach](http://msdn.microsoft.com/library/d4a80263-f3e0-4d81-9b61-f0cbeae3797b)   
 [Instrukcje: Tworzenie pary kluczy publiczny prywatny](http://msdn.microsoft.com/library/05026813-f3bd-4d7c-9e0b-fc588eb3d114)   
 [Strona podpisywania, Projektant projektu](../ide/reference/signing-page-project-designer.md)   
 [Wskazówki dotyczące wdrażania i zabezpieczeń ClickOnce](../deployment/clickonce-security-and-deployment.md)
