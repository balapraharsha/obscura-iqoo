# Obscura

**A dedicated camera privacy mode — select it like Photo or Video, and let it protect what shouldn't be captured.**

Built for iQOO Hackathon 2026 · Open Innovation Track · Team Codorithm

[Live Demo](https://balapraharsha.github.io/obscura-iqoo/) · [Pitch Deck](https://github.com/balapraharsha/obscura-iqoo/blob/main/Obscura_iQOO_Team_Codorithm.pptx) · [Video Walkthrough](https://drive.google.com/file/d/1sSEwgBvA1G4_6VYVnNMphOzZHqG5PWPo/view?usp=drive_link)

---

## The Problem

You frame one thing. Your camera captures everything else.

A casual photo at a café can quietly include a stranger's face, someone's open laptop screen, or a document left on the table — all before you ever notice. Once that photo is saved and shared, there's no way to undo it. The person in the background never consented to being photographed, and existing privacy tools only fix this *after* the damage is already done.

## What Obscura Does

Obscura is a dedicated capture mode — sitting alongside **Photo** and **Video** in the camera app — that continuously analyzes the live viewfinder for sensitive content. When Obscura Mode is active, detection and protection happen automatically: sensitive regions are masked **before** the final image is ever written to persistent storage.

> **Obscura moves privacy from after the photo to before the save.**

- **On-device NPU inference** — detection runs locally, no cloud round-trip
- **Automatic once selected** — no manual editing, no toggles to remember mid-shot
- **Capture-time protection** — the unprotected frame is never committed to storage

## How It Works

```
Live Viewfinder
      ↓
On-device NPU Detection  (faces · screens · documents)
      ↓
Privacy Mask Generation
      ↓
Shutter Pressed → Final Validation
      ↓
Localized Redaction Applied
      ↓
Protected Image Saved
```

AI performs detection locally; deterministic image processing applies the actual masking — keeping the pipeline fast, predictable, and easy to reason about.

## Detection Scope

| Category | Status |
|---|---|
| Bystander faces | 🟢 MVP |
| Screens (laptop, monitor, phone) | 🟢 MVP |
| Documents | 🟢 MVP |
| Children (extra sensitivity threshold) | ⚪ Future |
| License plates | ⚪ Future |
| Custom enterprise rule sets | ⚪ Future |

## Roadmap

**Today — MVP (Hackathon)**
Obscura ships as its own standalone app with a native-feeling `PHOTO / VIDEO / OBSCURA` mode selector. This is a deliberate choice: OEM-level camera pipeline access isn't publicly available for this hackathon, so Obscura is architected to slot in as a true native capture mode the moment that access exists.

**Future — Native Integration**
- Native OEM camera pipeline integration
- Custom redaction rules (family / enterprise modes)
- Signed, local audit log of redaction decisions
- Video capture support, not just stills

## Tech Stack

- **Platform:** Android (CameraX / Camera2)
- **On-device inference:** Local NPU-accelerated detection models
- **Processing:** Deterministic image redaction pipeline
- **No cloud dependency** — camera frames are never uploaded for analysis

## Why This Needs a Phone, Not a Website

- **Snapdragon NPU** — real-time frame classification at camera frame rate
- **Live camera feed access** — our app's own capture pipeline reads the viewfinder directly
- **On-device privacy** — the entire premise fails if a frame ever has to leave the phone

## Team Codorithm

- **Bala Praharsha Mannepalli** — Team Lead
- **Yasasswini Idimukkala**
- **Akshaya Siri Mannepalli**

Bala and Yasasswini have competed together across multiple national hackathons, including a Grand Finalist finish (Top 800 of 31,000+ teams) at the Meta PyTorch OpenEnv Hackathon × Scaler.

## Hackathon Context

Built for **iQOO Hackathon 2026 — Chennai City Battle**, Open Innovation track.

> Privacy shouldn't be a setting. It should be the default.

---

*This repository contains the prototype/website submitted as part of Team Codorithm's Phase 1 idea submission.*
