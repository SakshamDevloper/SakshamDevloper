# Save this file to: .github/workflows/metrics.yml in your SakshamDevloper/SakshamDevloper repo
#
# What it does:
# - Runs on a daily schedule (and on manual trigger) instead of regenerating on every
#   profile page load like typical stats badges do.
# - Renders three SVGs into a `dist/` folder on the `main` branch:
#     dist/isometric.svg    -> 3D isometric commit calendar
#     dist/languages.svg    -> language breakdown across your repos
#     dist/achievements.svg -> GitHub achievement unlocks
# - Commits them back to the repo automatically, which is what the README's
#   `raw.githubusercontent.com/.../main/dist/...svg` links point at.
#
# No secrets/tokens to configure manually — GITHUB_TOKEN is provided by Actions.

name: metrics
on:
  schedule:
    - cron: "0 3 * * *"   # daily at 03:00 UTC — edit as you like
  workflow_dispatch: {}    # lets you trigger it manually from the Actions tab

jobs:
  isometric:
    runs-on: ubuntu-latest
    steps:
      - uses: lowlighter/metrics@latest
        with:
          token: ${{ secrets.GITHUB_TOKEN }}
          user: SakshamDevloper
          template: classic
          base: ""
          plugin_isocalendar: yes
          plugin_isocalendar_duration: full-year
          output_action: gh-pages
          committer_branch: main
          filename: dist/isometric.svg

  languages:
    runs-on: ubuntu-latest
    steps:
      - uses: lowlighter/metrics@latest
        with:
          token: ${{ secrets.GITHUB_TOKEN }}
          user: SakshamDevloper
          template: classic
          base: ""
          plugin_languages: yes
          plugin_languages_analysis_timeout: 15
          plugin_languages_limit: 8
          committer_branch: main
          filename: dist/languages.svg

  achievements:
    runs-on: ubuntu-latest
    steps:
      - uses: lowlighter/metrics@latest
        with:
          token: ${{ secrets.GITHUB_TOKEN }}
          user: SakshamDevloper
          template: classic
          base: ""
          plugin_achievements: yes
          plugin_achievements_threshold: C
          committer_branch: main
          filename: dist/achievements.svg
