# ViMemory — Welcome Email (for Loops)

This is the email Loops sends **after** the user clicks the double-opt-in confirm link.
Set it up in Loops as a **Loop** triggered by "contact joins the `vimemory-waitlist` group" (or by form confirmation).

Replace the two placeholders before sending:
- `{{MSK_KEY}}` — the user's personal `msk_...` key. For now, mint it manually on the VPS (`manage.py adduser`) and paste it in per person, OR send a generic "your key is coming in a follow-up" version until auto-minting is built.
- `{{GATEWAY_URL}}` — your gateway endpoint, e.g. `https://vimemory.xyz`.

---

## Subject line options (pick one)

1. Your ViMemory key is inside
2. You're in. Here's everything to run ViMemory.
3. ViMemory — your key, your endpoint, your docs

**Recommended:** *You're in. Here's everything to run ViMemory.*

---

## Preview text (the gray line after the subject)

Your key, the endpoint, the install guide, and the open code — all in one place.

---

## Email body

Hey,

Thanks for confirming — you're in.

Here's everything you need to run ViMemory. No setup wizard, no sales call. Start on our gateway in a few minutes, and own it yourself whenever you're ready.

**1. Your secret key**

```
{{MSK_KEY}}
```

This is yours alone — your own isolated memory. Don't share it. It's capped at a few saves so you can feel how it works without any setup. When it fills, delete one to make room, or stand up your own server (below) for unlimited.

**2. Your endpoint**

```
{{GATEWAY_URL}}
```

Point Claude — or any model — at this, with your key, and start saving and recalling right away.

**3. The install guide (no coding required)**

You don't install anything by hand. You paste one prompt into Claude or ChatGPT and it walks you through setup, step by step.

→ Read the guide: https://vimemory.xyz/install.html

**4. The open code**

Nothing here is a black box. When you outgrow the trial and want your own server — unlimited memory, your data on your box, keys for your whole team — it's all open:

- Gateway (the server): https://github.com/arya-wtf/vimemory
- Local connector: https://github.com/arya-wtf/vimemory-localmcp

That's it. Save something in Claude, hit a limit, switch to another model, and your memory is already there.

If anything breaks, just reply to this email — a real person reads it.

— The ViMemory team

---

*P.S. ViMemory is a working build by Elux Space. If you've got a product, internal tool, or AI workflow that needs building right, that's our day job → https://www.elux.space*

---

## Notes for setup in Loops

- **Trigger:** contact confirms email (double opt-in) and lands in the `vimemory-waitlist` group — the form posts `userGroup: vimemory-waitlist`, which the AJAX script sends.
- **Double opt-in:** turn ON in Loops settings. This is what filters out dummy/throwaway emails — they can't click the confirm link.
- **The `{{MSK_KEY}}` problem:** Loops can't mint keys. Until you build auto-minting (a `/signup` route on the gateway), two options:
  1. **Manual:** Loops emails a "your key is being set up, arrives within X hours" version; you mint with `adduser` and send the key in a personal reply. On-brand ("we onboard a few teams at a time, personally").
  2. **Pre-mint a pool:** generate 50 keys, load them into Loops as a custom field, auto-insert one per contact.
- Keep the email plain-text-ish. It reads as a real person wrote it, which matches the brand and lands in the inbox (not promotions).
