---
title: Strumenti per la baseline di identità in Azure
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Strumenti per la baseline di identità in Azure
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/17/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: 5c06523d2b22293463d55f05c397dd55247f4369
ms.sourcegitcommit: bf9be7f2fe4851d83cdf3e083c7c25bd7e144c20
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/04/2019
ms.locfileid: "73566160"
---
# <a name="identity-baseline-tools-in-azure"></a>Strumenti per la baseline di identità in Azure

[Identity Baseline (Baseline di identità)](./index.md) è una delle [Five Disciplines of Cloud Governance (Cinque discipline della Governance cloud)](../governance-disciplines.md). Questa disciplina è incentrata sulla modalità di definizione dei criteri che garantiscono la coerenza e la continuità aziendale delle identità utente, indipendentemente dal provider di servizi cloud che ospita l'applicazione o il carico di lavoro.

Gli strumenti seguenti sono inclusi nella guida all'individuazione sull'Identità ibrida.

**Active Directory (locale):** Active Directory è il provider di identità usato più di frequente nell'organizzazione per archiviare e convalidare le credenziali utente.

**Azure Active Directory:** Un Software as a Service (SaaS) equivalente a Active Directory, in grado di eseguire la Federazione con un Active Directory locale.

**Active Directory (IaaS):** Istanza della Active Directory applicazione in esecuzione in una macchina virtuale in Azure.

L'identità è il piano di controllo della sicurezza IT. Di conseguenza, l'autenticazione è il Guard di accesso dell'organizzazione al cloud. Le organizzazioni hanno bisogno di un piano di controllo delle identità che ne rafforzi la sicurezza e tenga le app cloud al riparo dalle intrusioni.

## <a name="cloud-authentication"></a>Autenticazione cloud

La scelta del metodo di autenticazione corretto rappresenta la priorità assoluta per le organizzazioni che desiderano spostare le proprie applicazioni nel cloud.

Se si sceglie questo metodo, Azure AD gestisce il processo di accesso degli utenti. Affiancandolo a un accesso Single Sign-On trasparente, gli utenti possono accedere alle applicazioni cloud senza dover immettere nuovamente le proprie credenziali. Con l'autenticazione cloud è possibile scegliere tra due opzioni:

**Sincronizzazione dell'hash della password Azure ad:** Il modo più semplice per abilitare l'autenticazione per gli oggetti directory locali in Azure AD. Questo metodo si può anche usare con qualsiasi metodo, come metodo di autenticazione di un failover di backup, nel caso in cui il server locale sia inattivo.

**Azure ad dell'autenticazione pass-through:** Fornisce una convalida persistente delle password per i servizi di autenticazione Azure AD usando un agente software che viene eseguito in uno o più server locali.

> [!NOTE]
> Le società che per requisiti di sicurezza devono applicare immediatamente gli stati degli account utente locali, i criteri di gestione delle password e gli orari di accesso potrebbero usare questo metodo di autenticazione pass-through.

**Autenticazione federata:**

Quando si sceglie questo metodo, Azure AD passa il processo di autenticazione a un sistema di autenticazione attendibile separato, ad esempio Active Directory Federation Services locale (AD FS) o un provider di Federazione di terze parti attendibile, per convalidare la password dell'utente.

L'articolo [Scegliere il metodo di autenticazione appropriato per Azure AD](https://docs.microsoft.com/azure/security/azure-ad-choose-authn) contiene un albero delle decisioni per scegliere la soluzione migliore per l'organizzazione.

La tabella seguente riporta un elenco di strumenti nativi che possono aiutare a sviluppare i criteri e i processi che supportano la disciplina di governance.

<!-- markdownlint-disable MD033 -->

|Considerazioni|Sincronizzazione dell'hash delle password + Seamless SSO|Autenticazione pass-through + Seamless SSO|Federazione con ADFS|
|:-----|:-----|:-----|:-----|
|Dove si verifica l'autenticazione?|Nel cloud|Nel cloud dopo la verifica della password di protezione con l'agente di autenticazione locale|Locale|
|Quali sono i requisiti del server locale oltre il sistema di provisioning Azure AD Connect?|Nessuna|Un server per ogni agente di autenticazione aggiuntivo|Due o più server AD FS<br><br>Due o più server WAP nella rete perimetrale|
|Quali sono i requisiti per Internet locale e per la rete oltre il sistema di provisioning?|Nessuna|[Accesso a Internet in uscita](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-pta-quick-start) dai server che eseguono agenti di autenticazione|[Accesso a Internet in ingresso](https://docs.microsoft.com/windows-server/identity/ad-fs/overview/ad-fs-requirements) ai server WAP nel perimetro<br><br>Accesso di rete in ingresso ai server AD FS dai server WAP nelle reti perimetrali<br><br>Bilanciamento del carico di rete|
|Esiste un requisito per il certificato SSL?|No|No|Sì|
|Esiste una soluzione di monitoraggio dello stato?|Facoltativo|Stato agente fornito dall'[interfaccia di amministrazione di Azure Active Directory](https://docs.microsoft.com/azure/active-directory/hybrid/tshoot-connect-pass-through-authentication)|[Azure AD Connect Health](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-health-adfs)|
|Gli utenti ottengono l'accesso Single Sign-On alle risorse cloud dai dispositivi aggiunti al dominio all'interno della rete aziendale?|Sì, con l'[accesso Single Sign-On facile](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-sso)|Sì, con l'[accesso Single Sign-On facile](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-sso)|Sì|
|Quali tipi di accesso sono supportati?|UserPrincipalName + Password<br><br>Autenticazione integrata di Windows con [Seamless SSO](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-sso)<br><br>[ID di accesso alternativo](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-custom)|UserPrincipalName + Password<br><br>Autenticazione integrata di Windows con [Seamless SSO](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-sso)<br><br>[ID di accesso alternativo](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-pta-faq)|UserPrincipalName + Password<br><br>sAMAccountName + Password<br><br>Autenticazione integrata di Windows<br><br>[Autenticazione con certificato e smart card](https://docs.microsoft.com/windows-server/identity/ad-fs/operations/configure-user-certificate-authentication)<br><br>[ID di accesso alternativo](https://docs.microsoft.com/windows-server/identity/ad-fs/operations/configuring-alternate-login-id)|
|Windows Hello for Business è supportato?|[Modello di attendibilità chiavi](https://docs.microsoft.com/windows/security/identity-protection/hello-for-business/hello-identity-verification)<br><br>[Modello di attendibilità certificati con Intune](https://microscott.azurewebsites.net/2017/12/16/setting-up-windows-hello-for-business-with-intune)|[Modello di attendibilità chiavi](https://docs.microsoft.com/windows/security/identity-protection/hello-for-business/hello-identity-verification)<br><br>[Modello di attendibilità certificati con Intune](https://microscott.azurewebsites.net/2017/12/16/setting-up-windows-hello-for-business-with-intune)|[Modello di attendibilità chiavi](https://docs.microsoft.com/windows/security/identity-protection/hello-for-business/hello-identity-verification)<br><br>[Modello di attendibilità certificati](https://docs.microsoft.com/windows/security/identity-protection/hello-for-business/hello-key-trust-adfs)|
|Quali sono le opzioni di Multi-Factor Authentication?|[Azure Multi-Factor Authentication](https://docs.microsoft.com/azure/multi-factor-authentication)<br><br>[Controlli personalizzati con accesso condizionale*](https://docs.microsoft.com/azure/active-directory/conditional-access/controls#custom-controls-preview)|[Azure Multi-Factor Authentication](https://docs.microsoft.com/azure/multi-factor-authentication)<br><br>[Controlli personalizzati con accesso condizionale*](https://docs.microsoft.com/azure/active-directory/conditional-access/controls#custom-controls-preview)|[Azure Multi-Factor Authentication](https://docs.microsoft.com/azure/multi-factor-authentication)<br><br>[Server Multi-Factor Authentication di Azure](https://docs.microsoft.com/azure/active-directory/authentication/howto-mfaserver-deploy)<br><br>[Autenticazione a più fattori di terze parti](https://docs.microsoft.com/windows-server/identity/ad-fs/operations/configure-additional-authentication-methods-for-ad-fs)<br><br>[Controlli personalizzati con accesso condizionale*](https://docs.microsoft.com/azure/active-directory/conditional-access/controls#custom-controls-preview)|
|Quali stati dell'account utente sono supportati?|Account disabilitati<br>(fino a 30 minuti di ritardo)|Account disabilitati<br><br>Account bloccato<br><br>Account scaduto<br><br>Password scaduta<br><br>Orari di accesso|Account disabilitati<br><br>Account bloccato<br><br>Account scaduto<br><br>Password scaduta<br><br>Orari di accesso|
|Quali sono le opzioni di accesso condizionale?|[Accesso condizionale di Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)|[Accesso condizionale di Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)|[Accesso condizionale di Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)<br><br>[Regole di attestazione per AD FS](https://adfshelp.microsoft.com/AadTrustClaims/ClaimsGenerator)|
|Il blocco dei protocolli legacy è supportato?|[Sì](https://docs.microsoft.com/azure/active-directory/conditional-access/howto-baseline-protect-legacy-auth)|[Sì](https://docs.microsoft.com/azure/active-directory/conditional-access/howto-baseline-protect-legacy-auth)|[Sì](https://docs.microsoft.com/windows-server/identity/ad-fs/operations/access-control-policies-w2k12)|
|È possibile personalizzare il logo, l'immagine e la descrizione nelle pagine di accesso?|[Sì, con Azure AD Premium](https://docs.microsoft.com/azure/active-directory/customize-branding)|[Sì, con Azure AD Premium](https://docs.microsoft.com/azure/active-directory/customize-branding)|[Sì](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-federation-management#customlogo)|
|Quali scenari avanzati sono supportati?|[Smart Password Lockout](https://docs.microsoft.com/azure/active-directory/active-directory-secure-passwords)<br><br>[Report delle credenziali perse](https://docs.microsoft.com/azure/active-directory/active-directory-reporting-risk-events)|[Smart Password Lockout](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-pass-through-authentication-smart-lockout)|Sistema di autenticazione multisito a bassa latenza<br><br>[Blocco della Extranet di AD FS](https://docs.microsoft.com/windows-server/identity/ad-fs/operations/configure-ad-fs-extranet-soft-lockout-protection)<br><br>[Integrazione con i sistemi di gestione delle identità di terze parti](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-federation-compatibility)|

<!-- markdownlint-enable MD033 -->

> [!NOTE]
> I controlli personalizzati nell'accesso condizionale di Azure AD non supportano attualmente la registrazione dispositivo.

## <a name="next-steps"></a>Passaggi successivi

Il [white paper ibrido per la trasformazione digitale delle identità](https://resources.office.com/ww-landing-M365E-EMS-IDAM-Hybrid-Identity-WhitePaper.html) delinea le combinazioni e le soluzioni per la scelta e l'integrazione di ognuno di questi componenti.

[Strumento di connessione di Azure AD](https://aka.ms/aadconnectwiz) aiuta a integrare le directory locali con Azure AD.
