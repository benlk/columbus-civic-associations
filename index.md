---
title: Columbus Civic Associations
layout: home
---

<noscript>
    <p>This page offers the use of <a href="https://listjs.com/">List.js</a> to make the table below sortable and filterable.</p>
</noscript>

<div class="grid-row grid-gap">

<div class="tablet:grid-col-auto margin-bottom-1">
    <div class="usa-summary-box tablet:float-right tablet:width-card-lg" role="region" aria-labelledby="summary-box-key-information">
        <div class="usa-summary-box__body">
            <h4 class="usa-summary-box__heading" id="summary-box-key-information">
            About this list
            </h4>
            <div class="usa-summary-box__text">
                <p>This page provides a searchable list of civic associations and similar groups in the City of Columbus, Ohio.</p>
                <p>This list is sourced from the Columbus Department of Neighborhoods, and was last updated on March 28, 2025.</p>
                <p>This website is an unofficial presentation of the data and may contain errors. For more information, or to submit corrections, see the <a href="{% link about.md %}">About page</a>.</p>
            </div>
        </div>
</div>
</div>

<div class="tablet:grid-col-fill">
    <div id="list" class="">
        <label class="usa-sr-only" for="search-field">Search</label>
        <input class="search usa-search width-full margin-bottom-1" placeholder="Search" id="search-field" />
        <ul class="usa-button-group">
            <li class="usa-button-group__item usa-button-group__centering">
                Sort by:
            </li>
            <li class="usa-button-group__item">
                <button class="sort usa-button" data-sort="Organization">
                    Organization
                </button>
            </li>
            <li class="usa-button-group__item">
                <button class="sort usa-button" data-sort="Coalition">
                    Coalition
                </button>
            </li>
            <li class="usa-button-group__item">
                <button class="sort usa-button" data-sort="Email">
                    Email
                </button>
            </li>
            <li class="usa-button-group__item">
                <button class="sort usa-button" data-sort="Website">
                    Website
                </button>
            </li>
            <li class="usa-button-group__item">
                <button class="sort usa-button" data-sort="Facebook">
                    Facebook
                </button>
            </li>
            <li class="usa-button-group__item">
                <button class="sort usa-button" data-sort="Meeting">
                    Meeting
                </button>
            </li>
            <li class="usa-button-group__item">
                <button class="sort usa-button" data-sort="Meetingplace">
                    Meeting Place
                </button>
            </li>
        </ul>
        <div class="width-mobile">
            <table class="usa-table usa-table--stacked-header">
                <caption>List of Civic Associations</caption>
                <thead>
                    <tr>
                        <th scope="column" data-label="Organization">Organization</th>
                        <th scope="column" data-label="Active">Active?</th>
                        <th scope="column" data-label="Coalition?">Coalition</th>
                        <th scope="column" data-label="Contact">Contact</th>
                        <th scope="column" data-label="Email">Contact Email</th>
                        <th scope="column" data-label="Website">Website</th>
                        <th scope="column" data-label="Website">Facebook</th>
                        <th scope="column" data-label="Meeting">Meeting</th>
                        <th scope="column" data-label="Meeting Place">Meeting Place</th>
                        <th scope="column" data-label="Boundaries">Boundaries</th>
                        <th scope="column" data-label="Notes">notes</th>
                    </tr>
                </thead>
                <tbody class="list">
                {% for row in site.data.civics %}

                    {% if row['Active'] %}
                    {% if row['Active'] != "" %}
                        {% assign class_active = row['Active'] | slugify %}
                    {% endif %}
                    {% endif %}

                    <tr class="{{class_active}}" >

                    <th scope="row" class="Organization" data-label="Organization">
                        {{ row['Organization'] }}
                    </th>

                    <td
                        scope="row"
                        class="Active"
                        data-label="Active?"
                    >
                        {{ row['Active'] | capitalize }}
                    </td>

                    <td class="Coalition" data-label="Coalition">
                        {{ row['Coalition'] }}
                    </td>

                    <td
                        class="
                            Contact
                            {% unless row['FirstName'] or row['LastName'] %}display-none{% endunless %}
                        "
                        data-label="Contact"
                    >
                        {{ row['FirstName'] }}
                        {{ row['LastName'] }}{% if row['Title'] %}, {{ row['Title'] }}{% endif %}
                    </td>

                    <td
                        class="
                            Email
                            {% unless row['Email'] %}display-none{% endunless %}
                        "
                        data-label="Contact Email"
                    >
                        {% if row['Email'] %}
                            {{ row['email'] }}
                        {% else %}
                            (none)
                        {% endif %}
                    </td>

                    <td
                        class="
                            Website
                            {% unless row['Website'] %}display-none{% endunless %}
                        "
                        data-label="Website"
                    >
                        {% if row['Website'] %}
                            <a href="{{ row['Website'] }}" class="usa-link usa-link--external">
                                {{ row['Website'] | remove_first: "https://" }}
                            </a>
                        {% endif %}
                    </td>

                    <td
                        class="Facebook {% unless row['Facebook'] %}display-none{% endunless %}"
                        data-label="Facebook"
                    >
                        {% if row['Facebook'] %}
                            <a href="{{ row['Facebook'] }}" class="usa-link usa-link--external">
                                {{ row['Facebook'] | remove_first: "https://" }}
                            </a>
                        {% endif %}
                    </td>

                    <td
                        class="Meeting {% unless row['Meeting'] %}display-none{% endunless %}"
                        data-label="Meeting"
                    >
                        {{ row['Meeting'] }}
                    </td>

                    <td
                        class="Meetingplace {% unless row['Meetingplace'] %}display-none{% endunless %}"
                        data-label="Meeting Place"
                    >
                        {{ row['Meeting Place'] }}
                    </td>

                    <td
                        class="
                            Boundaries
                            {% unless row['North Boundary'] or row['East Boundary'] or row['South Boundary'] or row['West Boundary'] %}display-none{% endunless %}
                        "
                        data-label="Boundaries"
                    >
                        {% if row['North Boundary'] or row['East Boundary'] or row['South Boundary'] or row['West Boundary'] %}
                            <ul class="usa-list">
                                {% if row['North Boundary'] %}
                                    <li>North: {{ row['North Boundary'] }}</li>
                                {% endif %}
                                {% if row['East Boundary'] %}
                                    <li>East: {{ row['East Boundary'] }}</li>
                                {% endif %}
                                {% if row['South Boundary'] %}
                                    <li>South: {{ row['South Boundary'] }}</li>
                                {% endif %}
                                {% if row['West Boundary'] %}
                                    <li>West: {{ row['West Boundary'] }}</li>
                                {% endif %}
                            </ul>
                        {% endif %}
                    </td>

                    <td
                        class="notes {% unless row['notes'] %}display-none{% endunless %}"
                        data-label="Notes"
                    >
                        {{ row['notes'] | markdownify }}
                    </td>
                    </tr>
                {% endfor %}
                </tbody>
            </table>
        </div>
    </div>
</div><!-- /grid-col-fill -->

</div><!-- /grid-row -->


<script src="//cdnjs.cloudflare.com/ajax/libs/list.js/1.5.0/list.min.js"></script>
<script type="text/javascript">
var options = {
  valueNames: [
    'Organization',
    'Active',
    'Coalition',
    'Contact',
    'Email',
    'Website',
    'Facebook',
    'Meeting',
    'Meetingplace',
    'notes'
  ]
};

var associationsList = new List('list', options);
</script>,