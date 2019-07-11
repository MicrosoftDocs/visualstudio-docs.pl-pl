---
title: Dołączanie do portalu administratora subskrypcji programu Visual Studio po migracji
author: evanwindom
ms.author: jaunger
manager: evelynp
ms.date: 07/12/2018
ms.topic: conceptual
description: Dowiedz się, jak pomyślnie dołączyć organizacji po przeprowadzeniu migracji do portalu administratora subskrypcji programu Visual Studio.
ms.openlocfilehash: 68fe9621f602b9732ad54e94170125c840568ab1
ms.sourcegitcommit: 208395bc122f8d3dae3f5e5960c42981cc368310
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67784420"
---
# <a name="onboard-to-the-visual-studio-subscriptions-administration-portal-after-your-organization-is-migrated"></a>Dołączanie do portalu programu Visual Studio subskrypcje administracji po organizacji migracji

Jeśli zarządzane subskrypcje programu Visual Studio w Microsoft wolumin licencjonowania Service Center (VLSC), a ostatnio odwiedzających witrynę do zarządzania subskrypcjami, można zauważyć, że zarządzanie subskrypcjami nie jest już dostępna w witrynie VLSC. Proces, aby zarządzać subskrypcjami będzie mieć zapoznaniu się następująco:
> [!div class="mx-imgBorder"]
> ![Zrzut ekranu przedstawiający VLSC firmy Microsoft, za pomocą karty subskrypcje wyróżniony](_img/post-migration-onboarding/vlsc-subscriptions.png)

Jednak subskrypcje są teraz zarządzane za pomocą nowego portalu, nazywany portalem administratora subskrypcji programu Visual Studio. Zazwyczaj podstawowym lub uwagi dotyczące innych osobę kontaktową w zakresie umowy licencjonowania zbiorowego organizacji ukończenie tego procesu. W przeciwnym razie następujące informacje pomogą uzyskać dostęp do zarządzania subskrypcjami.

Może wystąpić jeden z kilku powodów:

1. [Głównej osoby kontaktowej nie ukończenia procesu dołączania.](#onboarding-not-completed-by-primary-contact)
2. [Głównej osoby kontaktowej ukończone dołączania, ale nie został dodany jako administrator. Poświadczenia zostały wymienione w witrynie VLSC.](#primary-contact-did-not-provide-you-administrator-access)
3. [Głównej osoby kontaktowej ukończone dołączania, ale nie został dodany jako administrator. Poświadczenia nie zostały wymienione w witrynie VLSC.](#your-credentials-were-not-listed-in-vlsc-prior-to-migration)

<sup>1</sup> Jeśli jesteś główną lub uwagi, skontaktuj się z pomocą i nie została ukończona procesu dołączania, należy wykonać kroki w scenariuszu, jeden w celu konfigurowania organizacji.

Poniższe sekcje zawierają więcej szczegółów na temat każdego z tych scenariuszy.

## <a name="onboarding-not-completed-by-primary-contact"></a>Dołączanie nie zostanie ukończone w głównej osoby kontaktowej

Jeśli głównej osoby kontaktowej nie zakończy się proces dołączania, zostanie wyświetlony następujący ekran. Jeśli masz dostęp do [wolumin licencjonowania Service Center (VLSC)](https://www.microsoft.com/Licensing/servicecenter/default.aspx), możesz ukończyć ten proces i uzyskać dostęp do zarządzania subskrypcjami. Będziesz potrzebować Twojej organizacji [numer klienta publicznego (PCN)](find-pcn.md), który znajduje się w witrynie VLSC.

Wprowadź w polu numer PCN [numeru PCN](find-pcn.md)i wybierz **Wyślij wiadomość E-mail z zaproszeniem**.
> [!div class="mx-imgBorder"]
> ![Zrzut ekranu portalu administratora subskrypcji programu Visual Studio](_img/post-migration-onboarding/send-invitation.png)

Otrzymasz wiadomość e-mail z unikatowego linku do ukończenia procesu dołączania. Kliknij link w wiadomości e-mail, zaloguj się przy użyciu adresu e-mail i jeszcze raz wprowadź numer PCN. Unikatowego linku w wiadomości e-mail to, co pozwala na uzyskanie dostępu do portalu administratora subskrypcji Visual Studio. Można, a następnie uzyskać dostęp i Zarządzaj subskrypcjami.
> [!div class="mx-imgBorder"]
> ![Zrzut ekranu sukces powiadomień](_img/post-migration-onboarding/email-success.png)

## <a name="primary-contact-did-not-provide-you-administrator-access"></a>Głównej osoby kontaktowej nie dostarczył możesz dostępu administratora

Jeżeli kontaktu podstawowego, ukończenie procesu dołączania, a poświadczenia wcześniej znajdowały się w witrynie VLSC głównej osoby kontaktowej nie zapewniają dostęp, zostanie wyświetlone następujące powiadomienie. Zostań administratorem, skontaktuj się z członkiem organizacji superadministratorów wymienionych w powiadomieniu.
> [!div class="mx-imgBorder"]
> ![Zrzut ekranu z programu Visual Studio portalu administratora subskrypcji, z listą superadministratorzy](_img/post-migration-onboarding/admin-list.png)

## <a name="your-credentials-were-not-listed-in-vlsc-prior-to-migration"></a>Poświadczenia nie zostały wymienione w witrynie VLSC przed migracją

Jeśli kontaktu podstawowego, ukończone procesu dołączania, ale nie został dodany jako użytkownik, poświadczenia nie zostały wcześniej wymienione w witrynie VLSC jest wyświetlone następujące powiadomienie. Dotrzyj do Twojej [głównej osoby kontaktowej](find-primary-contact.md) do uzyskania dostępu do portalu.
> [!div class="mx-imgBorder"]
> ![Zrzut ekranu programu Visual Studio portalu administratora subskrypcji, z powiadomieniem "nie można odnaleźć użytkownik"](_img/post-migration-onboarding/cant-find-you.png)